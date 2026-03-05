---
title: On AI and Fears About the Future
date: 2023-07-30T16:53:00+02:00
draft: false
tags:
  - large-language-models
  - artificial-intelligence
  - machine-learning
---

## Preamble

My thoughts are inspired by listening to Lex Fridman's podcast episode with Yuval Noah Harari[^1]. I really enjoyed listening to it, it was inspiring to me, thought provoking. Some arguments he made in the interview I don't fully subscribe to. I try to write down my thoughts about them here.

Roughly paraphrased I understood Harari's point on future risks of AI[^2] as follows:

- AI is a new type of tool: it can make decisions on its own and generate ideas on its own
- AI will likely understand us (humans) very well, but we don't understand it
- AI and bio-engineering might be used to induce change in humans to serve the nefarious ends of powerful, authoritarian regimes

## To point 3 - Technology Misuse

I agree. It sounds plausible to me that once the technology is available to gain an advantage, i.e. move closer to ones goals, it will be used in that way. Humans use them for "good" and for "evil". As an example: 1) AlphaFold from DeepMind is speeding up biology research to a new degree. 2) With the availability of crypto currencies and their ease of sending money via uncontrolled channels, cyber criminals had a hay day (see the influx of ransom ware attacks in the past 5 years). Similarly, we might observe how the generative text capabilities of large language models will be used to generate scam and phishing campaigns that will appear more authentic.

I cannot and don't want to forecast a trend how this might evolve with more capable technology. All I can see from my perspective, with my work experience in detecting malicious behavior in the digital domain, is that there always has been a cat and mouse game. Sometimes the mouse scored a lot of cheese before the cat could figure out the tactics to catch it, but the cat never starved. Therefore, while I see Harari's concerns I am vaguely optimistic that we will figure out ways to cope with it.

## To point 2 - Understanding

I am not sure what "breed" of AI Harari imagined in this interview. From my understanding no model is able to understand humans to the extent to manipulate them with intent. It is true that we don't know in detail how large language models gain their capability and generate their output after being trained on large quantities of text.

Where manipulation takes place, I'd argue, is in recommendation engines. Prominent examples are the systems that fill the feeds of Facebook, Twitter and YouTube. On a high level, here the systems are fed with user interaction data and set to predict certain desired outcomes, coupled with an optimization function. The manipulations comes from the desired target metric during the training of these systems. Not all aspects of that manipulation (one could also call it nudging or recommending in most cases) are intentional. This is because it is difficult to think the implication and effects of these systems through to the nth-degree. The reason for that lies in the complexity of the problem. The creators of these system have a goal in their mind and have to assume that the data they collect and the target they set will achieve that goal. The relationship between the training data, the target and the goal is not linear, not trivial, because it involves human behavior—in groups, not even just individual (if I learned one thing from my undergrad in economics its that we are really bad at predicting group interactions). One cannot think through this problem and come up with an equation to solve it, not at least with a proper serving of uncertainty.

That is why ML algorithms, equations that adjust parameters based on training data and an objective, are useful. With ML as a tool, there is no need to develop a theory and deduce a model from it. Instead it is a practical exercise to train the system, see where it fails and adapt from there. This exploratory approach brings along the fact that the map of its unintended side effects is incomplete.

ML systems do the thing they were trained to do. And as with all types of computer behavior, the computer follows what the human told it to do to the word, even if the human meant it another way. These large language models don't understand us the same way a good therapist would. They detect patterns and act according to their training.

## To point 1 - Decisions and Ideas

Again, I am not sure what Harari meant here.

### Decision Systems

Rule-based decision system were making decisions by themselves even before a wide adoption of ML systems in the domains he mentioned, credit and loan scoring. ML systems are in most cases better at that than hand-written rules.

I will now assume for the sake of argument that Harari meant that "AI" systems would follow their own agenda and base their decisions on that. In that case I don't know of evidence today that "AI" systems are capable of that. The agenda, i.e. objective or target, of those systems today is set by humans. As described in "to point two": ML systems fall to their level of training.

### Idea generation is different

A decision system backed by rules or a trained ML model for the application of credit scoring does not generate ideas. Even with large language models I'd say they are rehashing what they've learned and are not generating truly new ideas. But then comes the whole debate if humans are any different.

An example in the other direction could be AlphaFold. When it discovers new protein structures can one describe that as a new idea? Papers where written by humans before on such discoveries. I have a hard time to draw the analogy to systems like GPT-4. AlphaFold was specifically designed to do that and is in essence exploring the space of possible protein structure. We can generate new discoveries more efficiently than with the tools before. However, are all idea discoveries exploration of some space? I don't know. I feel this question is out of my area of expertise; might need to ask a psychologist and philosopher about that.

Nevertheless, I'm skeptic and hesitant to describe LLMs as they are today as idea generators.

[^1]: [Yuval Noah Harari: Human Nature, Intelligence, Power, and Conspiracies | Lex Fridman Podcast #390](https://lexfridman.com/yuval-noah-harari/)
[^2]: See from timestamp 2:06:59, "AI safety" in the episode
