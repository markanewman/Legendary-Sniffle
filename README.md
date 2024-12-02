This is a re-envisioning of a pre-step to a project I completed with a friend of mine[^10].

# Introduction

Making prompts for LLMs is easy.
Making prompts that return _exactly_ what you want [is hard](https://en.wikipedia.org/wiki/AI_alignment)[^07].

Design a method to create a better prompt for a simple task[^01][^03].

# Method

* Setup dev environment
* Setup 3 agents
  * Agent_Designer
  * Agent_Worker
  * Agent_Evaluator
* Agent_Designer designs several different prompts based on user input 
* Agent_Worker is supplied several documents, then runs of copies[^09] of each prompt.
  This is a disconnected task.
  * [Cosine similarity](https://en.wikipedia.org/wiki/Cosine_similarity) is used to determine if a prompt is stable[^08].
    Unstable prompts are discarded.
  * Clustering is used to group the results[^08].
    The prompt that created the most cental response is returned along with the result.
* Agent_Evaluator is asked how well Agent_Designer's goals were met

# Ops

Academic papers need to describe in detail how to repeat the experiment.
That can be a big ask to a neophyte.
Sometimes it is nice to be handed something and just play with it.

## Prerequisites

We will need the following installed:

1. [VS Code](https://code.visualstudio.com/)
2. [Docker Desktop](https://www.docker.com/products/docker-desktop/)
3. [Git](https://git-scm.com/)

## VS Code

I use [devcontainers](https://code.visualstudio.com/docs/devcontainers/containers) to allow a repeatable development experience.
The main burden this places on me is remembering to click `F1` before doing _any_ dev.
It buys other stuff too, but that is the main one.

1. Open the project in VS Code
   * On windows this is _usually_ done by opening the folder's context menu and selecting > More Options > Open in VS Code
2. Switch to _dev containers_
   * F1 > Dev containers: Rebuild and reopen in containers
   * Scaffolding file: `~/.devcontainer/devcontainer.json`
3. Start the debugger
   * `F5`
   * Scaffolding file: `~/.vscode/launch.json`
   * The debugging session is happening inside the dev container
4. Browse to _http://localhost/_
5. Play

## Powershell

Sometimes you don't want to update the code, just run it for a demo.
It also helps as a comparison to a cloud deploy.

1. Open Powershell
2. Navigate to the project folder
3. Build the image
   * `docker build -f ./.devcontainer/Dockerfile -t legendary_sniffle:latest .`
   * Notice that the `Dockerfile` and the build context are in different locations
4. Create and run the container
   * `docker run --rm -p 80:80 legendary_sniffle`
5. Browse to _http://localhost/_
5. Play

# Citation

To cite the original paper (preferred[^02]), use the following bib.txt:

> **TODO** - Add Cite block from Zi

To cite the re-envisioned _process_, use the above _and_ the following bib.txt:

> @misc{newman2024,
>  title={Legendary Sniffle},
>  author={Mark Newman},
>  year={2024},
>  url={https://github.com/markanewman/Legendary-Sniffle}
> }

[^01]: Just because I _think_ something is easy doesn't mean it actually is easy.
[^02]: A PhD in Data Science is a PhD in support.
       We don't get a lot of chances at 1st author.
       Zi is trying for tenure.
       I don't care about that.
[^03]: It bothers me that some people don't record their prompts[^05][^06] and seeds[^04].
[^04]: I understand that OpenAI doesn't guarantee the same prompt will give the [same response](https://cookbook.openai.com/examples/reproducible_outputs_with_the_seed_parameter).
[^05]: A chemist is not allowed to omit a reagent.
       Without a prompt, I can't replicate your work.
       That makes it bad science.
[^06]: From an industrial perspective, a prompt is a trade secret so it should _never_ be recorded.
[^07]: My small child has some interesting interpretations of what "completing" as task entails.
       We should not be surprised when our non-meat-based children do the same thing.
[^08]: I need a slider for threshing.
       See my comment[^4] about seeds.
[^09]: I need a slider for the number of copies.
       Running prompts costs money.
       I am unwilling to let the process say it needs a ton of copies.
       When I convert to a local RAG, this will go away.
[^10]: [@melhzy](https://www.github.com/melhzy)
