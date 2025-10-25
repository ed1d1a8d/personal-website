Welcome to my personal website.
I am a member of technical staff at the US Center for AI Standards and Innovation and a PhD candidate at MIT.
The overall goal of my work and research is to enable humanity to realize the benefits of advanced AI while adequately managing its downsides.

### Research Interests

Much of my previous work and thinking has been on adversarial robustness. I've thought about the phenomenon both in [simplified toy settings](https://dspace.mit.edu/handle/1721.1/139041) as well as in the setting of [superhuman](https://arxiv.org/abs/2211.00241) [game-playing agents](https://arxiv.org/abs/2406.12843). I'm interested in adversarial robustness for two key reasons:

- Adversarial robustness is very closely related to the worst-case performance of a system. Safe systems are ones which by definition have acceptable worst-case performance, so adversarial methods can serve as both a good auditing mechanism and as a training signal for safety.

- Our inability to steer advanced AI systems in a robust way reflects our inability to control the "core" values and tendencies of AI systems. For example, when RLHF is conducted on a LLM, it behaves aligned in the average case, but the existence of phenomena like "jailbreaks" shows that we have not effectively changed the "true" values of the system. Rather we have only instilled in it a bunch of heuristics that make it behave nice most of the time.

  I think working on robustness is a good way to improve our ability to do alignment of "core values".
  
  It might also be that this goal is ill-formed -- the intuition that generally intelligent systems have core values may be false and maybe the [hot-mess theory of intelligence](https://sohl-dickstein.github.io/2023/03/09/coherence.html) is right. Even in this pessimistic case, studying robustness could still give us highly decision-relevant knowledge about the nature of intelligence.

At the moment, I'm focusing on robustness in the vision domain as a stepping stone to robustness more broadly. My key focus is on developing techniques that can improve robustness against unrestricted adversaries. In the vision domain, I am particularly interested in how we can make progress on something like the [Unrestricted Adversarial Examples Challenge](https://github.com/openphilanthropy/unrestricted-adversarial-examples).

In the language domain, the question that interests me the most is this one: Given a natural language specification for how an AI system should behave, how can we build capable systems that robustly satisfy the specification? Ideas related to this question that interest me include [model specs](https://openai.com/index/introducing-the-model-spec/), scalable oversight, [relaxed adversarial training](https://www.alignmentforum.org/posts/atBQ3NHyqnBadrsGP/latent-adversarial-training), [representation engineering](https://arxiv.org/abs/2406.04313), [stateful defenses against adversaries](https://arxiv.org/abs/1907.05587), and [AI control](https://arxiv.org/abs/2312.06942).

Finally, a new topic I have been exploring recently is training AI systems to introspect on their own cognition. See [this blogpost](https://www.lesswrong.com/posts/EKhTrhrCz2rNg7FmG/) for some thoughts.

### Contact

If you would like to chat with me about the topics mentioned on this site,
please contact me at twang6 [at] mit [dot] edu.

Some links:
[Twitter](https://twitter.com/TonyWangIV),
[Google Scholar](https://scholar.google.com/citations?user=YWiob00AAAAJ),
[CV](docs/tony-wang-cv.pdf).

This page last updated: 2025-10-24.
