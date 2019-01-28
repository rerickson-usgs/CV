This is my (first) attempt at using the [vitae package](https://ropenscilabs.github.io/vitae/) to create a CV. 

I adapted some of Rob Hyndman's [example](https://github.com/robjhyndman/CV/) and thank him for sharing his code. 

Useful docker commands:
- Start: `docker run -d -p 8004:8787 -e PASSWORD=nowUse -v $(pwd):/home/rstudio -w /home/rstudio/  --name cv raerickson/r-cv`
- Build: ` docker build --rm --force-rm -t raerickson/r-cv .`

