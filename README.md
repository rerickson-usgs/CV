This is my (first) attempt at using the [vitae package](https://ropenscilabs.github.io/vitae/) to create a CV. 

I adapted some of Rob Hyndman's [example](https://github.com/robjhyndman/CV/) and thank him for sharing his code. 

Useful docker commands:
- Start: `docker run -d -p 8004:8787 -e PASSWORD=nowUse -v $(pwd):/home/rstudio -w /home/rstudio/  --name cv raerickson/r-cv`
- Build: ` docker build --rm --force-rm -t raerickson/r-cv .`

Stuff to include:

```
---
name: Richard A. Erickson
position: "Research Quantaitive Ecologist"
address: "Upper Midwest Environmental Sciences Center, US Geological Survey, La Crosse, WI"
phone:  608-781-6353
www: usgs.gov/staff-profiles/richard-erickson
email: "raerickson@gmail.com"
twitter: raericksonWI
github: rerickson-usgs
linkedin: raerickson 
date: "`r format(Sys.time(), '%B %Y')`"
headcolor: "000088"
output: vitae::hyndman
header_includes:
  - \ExecuteBibliographyOptions{useprefix=true}
  - renewcommand{\bibfont}{\normalfont\fontsize{10}{12.4}\sffamily}
---


# Overview 

I synthesis environmental and ecological data to guide natural resource managers. This requires the development of ecological theory in concert with quantitative tools. Additionally, I serve as a consulting statistician and R trainer.

# Research

My research focuses on anthropogenic impacts to natural systems. I studied the impacts of climate change on dengue disease dynamics for my MS research, pesticides on population dynamics for PhD, wind energy and white-nose syndrome on bats for my postdoctoral research, and currently study invasive species's impacts to ecosystems. In addition to studying impacts, I currently develop tools to assist in monitoring, assessing risk, and controlling invasive species. 

# Funding

I obtain the majority ($\sim 85\%$) through competitive funding. 
My current funding comes from USGS appropriated funds, USGS cyclical (competitive) funding, and external grants and awards. External sources have included the US Fish and Wildlife Service, the Department of Defense's Strategic Environmental Research and Development Program, the Great Lakes Restoration Initiative, and the US Army Corps of Engineers. 

# Techincal skills

My positions require me to stay current with cutting-edge technologies.  I primarily use R for statistical analysis and have written two packages. In addition to developing R courses, I am regularly consulted about R both inside and outside of USGS. I use Stan for Bayesian analysis and the USFWS consults with me for this software. I use Python for some population models on regular basis and the USFWS consults with me for this software. I use HTCondor for high-throughput computing and have delivered two invited presentations at HTCondor Week. I use Docker for reproducible results and sandboxing high-throughput computing and am consulted about its use within USGS. 


```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE, warning = FALSE, message = FALSE)
library(tidyverse)
library(RefManageR)
library(vitae)
source("baretable.R")
```

```{r bibfiles}
# Read any bib files
pubs <- ReadBib("works.bib", check = FALSE)
#reports <- ReadBib("rjhreports.bib", check = FALSE)
#packages <- ReadBib("Rpackages.bib", check = FALSE)
```
```{r read_in_files, echo = FALSE}
degrees <- read_csv("../degrees.csv")
jobs <- read_csv("../employment.csv")
other_positions <- read_csv("../other_positions.csv")
awards <- read_csv("../honors_awards.csv")
membership <- read_csv("../current_memberships.csv")
```
# Education

```{r education, results='asis'}
degrees %>% 
  baretable()
```
 
# Professional Positions 
```{r jobs, results='asis'}
jobs %>% 
  mutate(Years = paste(Start, "--", End, sep = "")) %>%
  select(Years, Position) %>%
  baretable()
```

# Other Positions
```{r other_positions, results = 'asis'}
other_positions %>% 
  mutate(Years = paste(Start, "--", End, sep = "")) %>%
  select(Years, Position) %>%
  baretable()
```

# Honors and Awards

```{r awards, results='asis'}
awards %>% 
  baretable()
```
```
