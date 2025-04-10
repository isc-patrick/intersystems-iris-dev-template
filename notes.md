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
1. There was a day long maintenance window for github codespaces in February and one in April. I see no calendar of futre events, but there previous possible service interruptions gave only a week warning. Search for 'Scheduled Codespaces maintenance'
2. Github team uses Codespaces for dev work extensively: https://github.blog/engineering/infrastructure/githubs-engineering-team-moved-codespaces/
3. Technically the devcontainer that is the basis for the codespace is the same as the one used for local development, so it can be run on your local machine as well with VSCOde