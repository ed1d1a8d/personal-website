Welcome to my personal website.
I'm a 3rd year PhD student at MIT, where I spend my time thinking about how humanity can build friendly AGIs (without greatly harming itself in its attempt to do so).

### Research Interests

Much of my previous work and thinking has been on adversarial robustness. I've thought about the phenomenon both in [very simplified toy settings](https://dspace.mit.edu/handle/1721.1/139041) as well as in the setting of [superhuman game-playing agents](https://arxiv.org/abs/2211.00241). I'm interested in adversarial robustness for two key reasons:

- Adversarial robustness is very closely related to the worst-case performance of a system. Safe systems are ones which by definition have acceptable worst-case performance, so adversarial methods can serve as both a good auditing mechanism and as a training signal for safety.

- Our inability to steer advanced AI systems in a robust way reflects our inability to control the "core" values and tendencies of AI systems. For example, when OpenAI RLHF's GPT-4, it behaves aligned in the average case, but the existence of jailbreaks shows that we have not effectively changed the "true" values of the system. Rather we have only instilled in it a bunch of heuristics that make it behave nice most of the time.

  I think working on robustness is a good way to improve our ability to do alignment of "core values".
  
  It might also be that this goal is ill-formed -- the intuition that generally intelligent systems have core values may be false and maybe the [hot-mess theory of intelligence](https://sohl-dickstein.github.io/2023/03/09/coherence.html) is right. Even in this pessimistic case, studying robustness could still give us highly decision-relevant knowledge about the nature of intelligence.

At the moment, I'm working on robustness in both the vision and language domains. My key focus is on developing techniques that can improve robustness against unrestricted adversaries. In the vision domain, I am particularly interested in how we can make progress on something like the [Unrestricted Adversarial Examples Challenge](https://github.com/openphilanthropy/unrestricted-adversarial-examples). In the language domain (where most of my efforts are right now), I want to answer the following question:

<p style="text-align: center;"><b>What are the core difficulties with preventing jailbreaks in language models,<br>and how can these difficulties be overcome?</b></p>

My current take is that the answer involves scalable oversight and possibly [relaxed adversarial training](https://www.alignmentforum.org/posts/atBQ3NHyqnBadrsGP/latent-adversarial-training).

A north star for my research agenda is to develop techniques that could let us
reliably instill Asimov's three laws into future AGI systems.

### Contact

If you would like to chat about anything I've mentioned on this site,
feel free to contact me at
twang6 [at] mit [dot] edu.

Some links:
[Twitter](https://twitter.com/5kovt),
[Google Scholar](https://scholar.google.com/citations?user=YWiob00AAAAJ),
[CV](docs/tony-wang-cv.pdf).
