This is a re-invisioning of a project I completed with[^02] a friend of mine (TODO: add in Zi's GitHub)

# Introduction

Making prompts for LLMs is easy.
Making prompts that return _exactly_ what you want [is hard](https://en.wikipedia.org/wiki/AI_alignment)[^07].

Design a method to create a better prompt for a simple task[^01][^03].

# Method

* Setup dev enviorment
* Setup 3 agents
  * Agent_Designer
  * Agent_Worker
  * Agent_Evaluator
* Agent_Designer designs several different prompts based on user input 
* Agent_Worker is supplied several documents, then runs of copies[^09] of each prompt.
  This is a disconnected task.
  * [Cosine similarity](https://en.wikipedia.org/wiki/Cosine_similarity) is used to determin if a prompt is stable[^08].
    Unstable prompts are discarded.
  * Clustering is used to group the results[^08].
    The prompt that created the most cental response is returned along with the result.
* Agent_Evaluator is asked how well Agent_Designer's goals were met

TODO: Add Cite block from Zi

[^01]: Just because I _think_ somethign is easy dosent mean it actually is easy.
[^02]: A PhD in Data Science is really a PhD in support.
       Zi has his PhD in Data Science too, but he it trying for tenure, I am not.
       He needs 1st authorship.
       I don't care if I am last in a dozen authors.
[^03]: It bothers me that some people don't recoard their prompts[^5][^6] and seeds[^4].
[^04]: I understand that OpenAI dosen't gurentee the same prompt will give the [same response](https://cookbook.openai.com/examples/reproducible_outputs_with_the_seed_parameter).
[^05]: A chemist is not allowed to omit a reagent.
       Without a prompt, I can't replicate your work.
       That makes it bad science.
[^06]: From an industral perspective, a prompt is a trade secret so it should _never_ be recorded.
[^07]: My small child has some intresting interpreations of what "completing" as task entails.
       We should not be supprised when our non-meat-based childern do the same thing.
[^08]: I need a slider for thresholding.
       See my comment[^4] about seeds.
[^09]: I need a slider for the number of copies.
       Running prompts costs money.
       I am unwilling to let the process say it needs a ton of copies.
       When I convert to a local RAG, this will go away.
       

