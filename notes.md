__Codespace Evaluation__
Evaluate the use of github Codespace for GenAI workshop.

__Notes__
 - I have a codespace template that launches 2 containers: IRIS and a Jupyter notebook. Jupyter and the IRIS SMP can be accessed via forwarded ports. For an Interactive step through style workshop the easiest method would probably be to just create a set of simple html pages with the content and it would not require a server
 - We can choose from 2,4,8 CPUS and 8, 16, 32 GB RAM VMs as hosts.
 - With a cold start, the VM takes about 5 minutes to start. Pre-building the template brings that to under 30 seconds.
 - Intersystems can fairly easily allow the workshop participants to start their own codespaces and not have to pay for the resources, https://docs.github.com/en/codespaces/managing-codespaces-for-your-organization/choosing-who-owns-and-pays-for-codespaces-in-your-organization
 - Instance sizes allowed to be deployed can be limited, https://docs.github.com/en/codespaces/managing-codespaces-for-your-organization/restricting-access-to-machine-types
 - The code editor is just the VSCode web editor so the dev experience, intellisense, auot-formating is good.


__Risks, Concerns, Reliability__
1. There was a day long maintenance window for github codespaces in February and one in April. I see no calendar of future events, but there previous possible service interruptions gave only a week warning. Search for 'Scheduled Codespaces maintenance'
2. Github team uses Codespaces for dev work extensively: https://github.blog/engineering/infrastructure/githubs-engineering-team-moved-codespaces/
3. Technically the devcontainer that is the basis for the codespace is the same as the one used for local development, so it can be run on your local machine as well with VSCode



__Potential paths of Workshop by Theme__
Test First Approach

1. First Principals(short version): GENAI App primary components
   1. LLM interface: Function that takes a string and returns a string
   2. Prompts and Prompt Templates
   3. RAG
   4. Tools
   5. Memory/Context
   6. Workflow
   7. Agents
   8. UI

2. First Principals: Break down the common components of an LLM based application into simple terms and implementations
   1.  Test-First development
       1.  The success of any LLM based application can only be determined by the evaluation metrics being used to assess it. General benchmarks are not useful for any specific solution. This is 10 fold more important than testing(unit, integration tests) of standard application logic due to the inherent variability, which is primarily a consequence of #2.
       2.  This can be done in a very iterative and qualititative way which means that after setting up some basic infrastracture can be done with a minimal amount of fully controllable effort.
       3.  Testing on different LLMs is critical for revealing LLM specific behavior, avoiding vendor lock-in, performance and cost optimizations and generally not sticking your app in the mud in this fast changing and evolving ecosystem.
   2.  An LLM  is a function that takes a string and returns a string. Both exist within a practically infinite space
        ```python
        def llm(message: str) -> str:
            return process(message)
        ```
    3. A Prompt is the string you send and is created via a Prompt Template
    4. RAG is the process of enriching the Prompt with content related to the user's message. This is done by searching through content using some style of vector search.
    5. Tools are dynamically invoked functions.
       1. Most libraries hide what is happening in this step and that is bad. This pattern is critical to using LLMs and should be explicitly stated instead of hidden. This works by asking the LLM for structured output
    6. Memory/Context is a general method for maintaining continuity in a conversation often involving RAG.
    7. A Workflow is a set of steps executed in a event driven environment.
       1. Some systems use DAG's(Directed Acyclical Graphs) for workflows. We don't think this is a good idea for 2 reasons: It always feels forced to thing about a workflow as a graph(nodes and edges vs steps and events) and many workflows, especially with LLMs, are explicitly cyclical, repeating some cycle with a predetermined number of cycles or a stopping condition.
    8. An Agent uses Memory, Tools and RAG to execute one or more workflows.
       1. When using only one Agent, it is often the same thing as a Workflow. See how this is true in LLamaIndex:https://github.com/run-llama/python-agents-tutorial
    9. UI
       1.  CL REPL
       2.  Web UI
    10. ??These simplifications can be debated, but are generally useful in thinking about the process
        1.  Within often ambiguously defined, fast moving domains like GenAI, implementations greatly vary in their language and how they might define these topics. This aligns best with LlamaIndex.
        2.  Here is how a group at MIT addresses the question of what is an AIAgent, 
            What is an “AI agent”?
            https://aiagentindex.mit.edu/
            There is no agreed upon definition of the term. The notion of artificial agency has a long and contentious history across multiple disciplines. There have been many attempts to define the term “agent”, but we do not decide among prior definitions or offer our own.
