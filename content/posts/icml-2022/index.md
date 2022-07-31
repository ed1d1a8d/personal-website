---
title: "ICML 2022"
subtitle: Cool papers and my takeaways
date: 2022-07-26
lastmod: 2022-07-30
draft: true
tags:
  - machine-learning
---

# Stand out papers

## Datamodels{{<sidenote >}}
[Datamodels: Predicting Predictions from Training Data, by Ilyas et al.](https://arxiv.org/abs/2202.00622)
{{< /sidenote >}}

Let $D = \\{(x_1, y_1), \ldots, (x_n, y_n)\\}$ be a dataset of labeled images,
where $x_i \in \mathcal{X}$ are images and $y_i \in \mathcal{Y}$ are labels.
Let $S$ be a subset of $D$,
and let $\mathcal{A}$ be a learning algorithm
that uses $S$ as training data
and outputs a classifier $f_\mathcal{A}(\\,\cdot \\,;\\, S): \mathcal{X} \to \mathbb{R}^{|\mathcal{Y}|}$,
which takes an image as input and outputs logits.

The datamodels paper studies the following question:
**What is the behavior of $f_\mathcal{A}(\\,\cdot \\,;\\, S)$
as a function of $S$ ?**

The paper shows that when $\mathcal{A}$
corresponds to training a DNN classifier via SGD,
the *margin*{{< sidenote >}}
The *margin* of a logit-output classifier
$f:\mathcal{X} \to \mathbb{R}^{|\mathcal{Y}|}$
on a datapoint $x$ with true label $y$
is defined as
`f(x)[y] - max(f(x)[i] for i in Y if i != y)`.
{{< /sidenote >}}
of $f_\mathcal{A}(\\,\cdot \\,;\\, S)$ on $x$
can be extremely well-approximated by a linear function
$g^\theta_x: 2^D \to \mathbb{R}$ of the form
$$
g^\theta_x(S) = \sum_{i=1}^n \theta_i(x) \cdot \mathbb{1}((x_i, y_i) \in S).
$$
The authors call $g^\theta_x$
a *linear datamodel*,
and find (with a lot of compute)
linear datamodels that satisfy
$g^\theta_x(S) \approx f_\mathcal{A}(x\\,\cdot \\,;\\, S)$
for a wide range of $x$ and $S$ (on CIFAR10 and FMoW).
The authors have this mic-drop of plot:
{{<
    figure
    src="res/datamodels.png"
    width="250px"
    caption="A linear datamodel demonstrating an extremely strong ability to predict the behavior of DNNs trained on a subsets of CIFAR10 data. $\alpha = |S| / |D|$ measures how big $S$ is. (Taken from Figure 5 in the paper)."
>}}


### Equivariance versus augmentation, [Gerken et al.](https://arxiv.org/abs/2202.03990)

### Adversarial robustness of biological neurons, [Guo et al.](https://arxiv.org/abs/2206.11228)

### Model soups{{<sidenote >}}
[Model soups: averaging weights of multiple fine-tuned models improves accuracy without increasing inference time, by Wortsman et al.](https://arxiv.org/abs/2203.05482)
{{< /sidenote >}}

```python
def uniform_soup(ms: list[Model]) -> Model:
    return Model(weights=sum(m.weights for m in ms) / len(ms))

def greedy_soup(ms: list[Model]) -> Model:
    # Sort models in decreasing order of validation accuracy
    sorted_models = sorted(models, key=lambda m: val_acc(m), reverse=True)

    # Greedily add models as long as validation accuracy keeps going up
    chosen_models = []
    for m in sorted_models:
        if (  val_acc(uniform_soup(chosen_models + [m]))
            > val_acc(uniform_soup(chosen_models)) ):
            chosen_models.append(m)

    return uniform_soup(chosen_models)
```

{{<
    figure
    src="res/model-soup.png"
    width="400px"
    caption="The grey hexagon is CLIP ViT-B/32, the green diamonds are CLIP ViT-B/32 finetuned on ImageNet with different hyperparameters, the blue dot is the uniform soup of all the finetuned models, and the purple star is the greedy soup of all the finetuned models. The distribution shift datasets are ImageNetV2, ImageNet-R, ImageNet-Sketch, ObjectNet, and ImageNet-A."
>}}

TODO: Comment on relationship with ensembling. Pose question of why ensemble models are good.
