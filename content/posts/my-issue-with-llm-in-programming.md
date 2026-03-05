---
title: My Issue With LLM in Programming
date: 2023-03-22
draft: false
tags:
  - large-language-models
  - artificial-intelligence
---

There are organizations ([example](https://www.numbersstation.ai/post/fine-tuning-a-gpt-llm-to-sql-for-enterprise-use-cases), nothing in particular about this Org, I stumbled over their blog post recently, which inspired the thoughts below) trying to build LLM-based systems that can program. In the example posted above they describe the difficulties with LLM and accessing real-word applications like databases.

> The main issue that exists is hallucination. LLMs can write SQL, but they are often prone to making up tables, making up fields, and generally just writing SQL that if executed against your database would not actually be valid. So one of the big challenges we face is how to ground the LLM in reality so that it produces valid SQL. The main idea to fix this (we will go into more detail below) is to provide the LLM with knowledge about what actually exists in the database and tell it to write a SQL query consistent with that. However, this runs into a second issue - the context window length. LLMs have some context window which limits the amount of text they can operate over. This is relevant because SQL databases often contain a lot of information. So if we were to naively pass in all the data to ground the LLM in reality, we would likely run into this issue. A third issue is a more basic one: sometimes the LLM just messes up. The SQL it writes may be incorrect for whatever reason, or it could be correct but just return an unexpected result. What do we do then? Do we give up?

Without being able to prove it, I think that we cannot simply let LLMs write the entire script. Programming languages (counting SQL as one in this case) are structured, filled with rules and require precision. LLMs cannot provide that 100% of the time.

There is the argument that humans can't do it either, and to this I'd respond that first, a human can self-check if the code they are writing is working and second, someone else needs to prove-read and try out that code. Or, we want to live dangerously and push straight to production without tests and reviews.

The next argument pro-LLM use is that it should augment the human. Yes, I agree, but nothing I've seen so far comes close to a good integration. What, in my opinion, would be helpful is to have a LLM system be at the the stage in the UX as linters and static code checkers. This would require LLMs to be much more dependable and not like a junior dev. Example: Pylint is great at telling me where and how my Python code violates its rules. Sometimes it even suggests a fix. Pylint was built by humans, agreeing on these rules. Now imaging a LLM-based refactoring assistant that could suggest improvements towards clean-code and higher performance and is tied to certain rules. In this case I want to avoid halucinations. As a developer I don't need another source of uncertain suggestions, my brain is likely providing enough of those.

The longer I think about it, the more I think the hopes, visions and goals we base on the current capabilities of LLMs don't stand on robust ground. LLMs have capabilities and we don't understand their extent. We don't know their failure modes and where we can trust them. For all that more research is required. This can take the form of companies integrating them and failing and of academics methodically figuring them out. But as a business that has no expertise and willingness to dive deep into LLMs, I would not go that route and rather build/use proven, boring software.
