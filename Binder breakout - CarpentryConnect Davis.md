---
tags: dibsi18, binder
---
# Binder breakout - CarpentryConnect Davis 
---
#### Github IDs
Ming Tang: @crazyhottommy (I know I should change it...but stucked)
Dana Miller: @dmgt
Gail Coletedflins: @repositorian
More people: Yuvi, Gail, Abigail, Sateesh, Titus...

---
Outline from Carol and Titus' Binder talk + demo at CarpentryConnect: https://hackmd.io/s/S1fWYzBfQ#

#### Ideas from breakout planning: 
- Write up Binder setup process from yesterday
    - **Docs in progress [here](https://hackmd.io/qol_olKmTmi_TaLk2UuZSA#)**
    - **Upload screenshots** [here](https://github.com/dmgt/binder_tutorial_screenshots) (can move elsewhere if helpful)
    - First by forking example [here](https://github.com/binder-examples/r) (in R but pretty similar for other examples)
        - Add note on how to open with RStudio instead of Jupyter in Binder
    - Then how to binderize an existing repo with R code 
        - Hao did this [here](https://github.com/ha0ye/Power_of_Irma)

- Try setting up Binders for different use cases (add use cases you are excited about below!)
- Collect questions (useful for development of FAQ and feedback for [upcoming Binder workshop](https://github.com/dib-lab/CarpentryConWest18/issues/4#issuecomment-400768559) in Birmindham )


### Questions
*(collect  here, both for today and longer term to turn into FAQ)*

#### Paraphrasing  clarifying q's from Binder novices and peer attempts to answer
- Q: When a Binder is being built, is that compute happening on our local laptops or on mybinder.org's servers? A: latter (even though the build log is visible on your screen)
- Q: Do I have to have RStudio or python installed on my computer to build a Binder or to open one? (not obvious since most people had these installed already) A: No,  Response: Wow, how cool!
- Q: Why isn't RStudio explicitly specified as something that has to be included in the Binder when we specify the version of R and the R packages? A: Binder includes by default when R is included (?)
- Q: When I fork an example Binder from `binder-examples`, and launch it without making any changes, will it still have to rebuild any why? A: Yes, it will rebuild a new image from scratch, your github username is part of the url path, and it is now different
- Q: What *is* a container and why are they useful? Assume learners have not heard of containers before. Helpful to briefly explain that Docker is a tool for containers, and the shipping industry metaphor of standardizing shapes/packaging for interoperability
- Q: My workflow includes python, R, and bash, can that be binderized? 
- Q: Is there a way to launch a binder other than manually pasting in the URL to mybinder.org? A: Yes, the url in the button link

#### Q's about building Binders
-  If you want to binderize a repo with existing R code from scratch, what requirements do you need to have in your repository to create a binder? Ex. what does your runtime.txt have to include? 
    - For example, learners were surprised can can binderize a .ipynb file in a repo with no other dependancies specified, because Binder automatically gives you a Jupyter 3 environment

- What's a good workflow for using branches to get around binder rebuilding? Can I point binderhub to `master` branch of a repo, and then keep pushing changes to `dev` and then merging over to `master` when I want the docker image to be rebuilt?
- Can I extract the docker image from a built binder link so that I can put it into my repo and not have to worry about the image to be rebuilt on each change to the repo?

- Idea for checklist for "If I am going to put the code for my next paper on GitHub and also Binderize it what are the minimum best practices for what to include in the repo"
    * RStudio instructions:
        - list packages in `install.R` (would be nice to have a plugin for `devtools` to translate a `DESCRIPTION` file from R packages or R compendia into a `install.R` file)
        - list R version in `runtime.txt` (refers to a build version from MRAN -- what are the possible options?)
        - build from mybinder.org
        - take the binder link, append `?urlpath=rstudio`
        - Also see this issue on being able to open a specific Rmarkdown file within RStudio using a binder link: https://github.com/jupyterhub/binderhub/issues/325

- What are the ways to get data into/out of Binders?
    - Eg can use "Upload File" inside RStudio
    - What if data requires some authorization token eg for AWS or OrchidID, does that mean the data can not be automatically included in the Binder? 

#### Q's about hosting Binders
- Helpful to be *very clear* about which urls are persistant (eg url to open a binder)  and which are session-specific (eg the url for a particular binder instance once it opens)

- Amoung many other ideas (libraries, journals, data repositories etc), can there be a setup so that a researcher can binderize a repo for the code for their paper, and charge the compute credits to their Jetsream allocation?

#### Q's about teaching / encouraging Binder use?

- What are known limitations of Binder it's important for prospective users to be aware of?
    - Eg ephemeral (don't use for a day-long workshop)
    - Eg can demo code used to generate figures for an experient, not appropriate for re-running computationally-intensive  steps
    - Eg an entire classroom trying to build new Binders at once is probably not a good idea
    - What else?

- Suggestion for docs to include motivating examples at start for people who don't know what Binder is or why they'd use it yet

### Collecting examples of Binder use cases
- [List from workshop last year](https://github.com/ctb/2017-binder-workshop-notes/blob/master/Binder%20workshop%20in%20flight%20-%20schedule,%20links,%20etc.md#use-cases-for-binder)
- Preview data from a data repository before download?
- Share visualization / Jupyter widgit / Shiny with collaborator who does not and may never use R/python?

### Other links and resources
- [List of known BinderHub deployments](https://binderhub.readthedocs.io/en/latest/known-deployments.html)


### Top 3 challenges and opportunities

Things we did!
- Worked on "making your first binder" materials 
- Re-tested binder deployment and changing the README to open rstudio for the binder
- Tested the littlest jupyter hub deployment on jetstream
- Discussed the practical need for containers in reproducible research

* Challenges
    * 1. scaling up (# of instances and memory)
    * 2. More canonical material for 'getting started with MyBinder.org'
    * 3. Easier UI for launching into RStudio than what we have on MyBinder.org
* Opportunities
    1. Teaching R and Shell inside the same Rstudio setup.
        - I tried using git to make changes to a repo from within the RStudio shell and ran into trouble pushing changes back to GH. Not sure if this was an authentication error or not; capability would be a nice platform for doing work directly within a binder session (possible use case - working on a machine with internet access but without dev applications installed).
    2. Making your data analysis reproduciable for others.
    3. Interest in a checklist for "If I am going to put the code for my next paper on GitHub and also Binderize it what are the minimum best practices for what to include in the repo"
    
    4. Test 'The Littlest JupyterHub', a new simple to set up JupyterHub distribution for people of all skill levels! Talk to Yuvi :)
