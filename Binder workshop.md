Binder workshop
===============

[Back to master schedule](https://hackmd.io/kt_gMYKIQz2MbloD9mSCyQ)

## Forget about reading, let's do something!

1. Go to https://github.com/binder-examples/r

2. Click on "launch RStudio"

3. Run the following commands in RStudio:
 
```
library("tidyverse")

download.file("https://ndownloader.figshare.com/files/2292169",
              "data/portal_data_joined.csv")

surveys <- read.csv("data/portal_data_joined.csv")

surveys_complete <- surveys %>%
  filter(!is.na(weight),           # remove missing weight
         !is.na(hindfoot_length),  # remove missing hindfoot_length
         !is.na(sex))                # remove missing sex
		 
## Extract the most common species_id
species_counts <- surveys_complete %>%
    count(species_id) %>% 
    filter(n >= 50)

## Only keep the most common species
surveys_complete <- surveys_complete %>%
  filter(species_id %in% species_counts$species_id)
  
write_csv(surveys_complete, path = "data_output/surveys_complete.csv")

```

Now let's make a new binder with this data `data_output/surveys_complete.csv` already installed!

Once it's built, you'll need to set `?urlpath=rstudio`  to run RStudio Web.

Then, go to [data viz in R ecology lesson](http://www.datacarpentry.org/R-ecology-lesson/04-visualization-ggplot2.html) and try running!

----

If you are interested in the rules for what gets installed, check out [the config file documentation in repo2docker](https://repo2docker.readthedocs.io/en/latest/config_files.html).

----

Here is the 3 hr workshop:

https://github.com/ngs-docs/2018-ggg-rstudio-bioinformatics-ws/

## Back to reading: what is Binder?

- It's a service
    - https://mybinder.org
- It's a way to display your work (Jupyter notebooks and more)
    - https://binderhub.readthedocs.io/en/latest/overview.html
    - A clickable badge in a GitHub repo too
- It's a project (BinderHub) that you can deploy
    - https://binderhub.readthedocs.io/en/latest/

## Give it a Try

1. If you are new to Jupyter notebooks and/or GitHub https://try.jupyter.org
2. Check out a fun notebook: https://github.com/willingc/ThinkDSP
3. Build a Binder
    - Find a repo with notebooks
    - Go to https://mybinder.org
    - Enter repo information in the form and click `Launch`
    - Wait a short while while a temporary Docker container is built in the cloud for you
    - See the Jupyter file browser and select the notebook to open

## Build your own BinderHub

Yes, yes you can!

We had a workshop here last year where we did this.

1. Understand what you are building
    - Try https://mybinder.org if you haven't already
    - View the components that make up a BinderHub and some high-level architecture illustrations: https://binderhub.readthedocs.io/en/latest/overview.html

2. What you need to be successful
    - Understand how to use shell and command line
    - Know git and GitHub basics
    - A peer (pair-programming is encouraged, especially if you are still learning above)

3. Get the documentation, each in its own browser tab
    - BinderHub | [docs](https://binderhub.readthedocs.io/en/latest/) | [repo](https://github.com/jupyterhub/binderhub/)
    - Zero to JupyterHub | [docs](https://zero-to-jupyterhub.readthedocs.io/en/latest/) | [repo](https://github.com/jupyterhub/zero-to-jupyterhub-k8s)
    - repo2docker | [docs](https://repo2docker.readthedocs.io/en/latest/) | [repo](https://github.com/jupyter/repo2docker)

4. Let's install
    - [Zero to BinderHub](https://binderhub.readthedocs.io/en/latest/#zero-to-binderhub)

## Resources

Andrea Zonca, SDSC - https://zonca.github.io
   - jetstream blog posts about JupyterHub

