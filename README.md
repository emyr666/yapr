# yapr
yapr : pronounced 'yapper' this is 'yet another pipeline runner'

There are many pipeline runners in use. These range from being quit light and requiring a lot of user code to being fully fledged web frameworks that allow drop in of pipelines from external supporters and can be completely driven by GUI.

Examples (not exhaustive):
* Nextflow (with or without Nextflow Tower)
* vr-pipe
* snakemake
* galaxy
* arvados

With regards to workflow languages, there are now 3 main ones in use, CWL, WDL and nextflow's DSL.

All of these have advantages and disadvantages. At CNAG in particular an in-house system called jip has been used but this has suffered from a lack of maintenance and further development over the years.

This project may end up with an actual concrete piece of software or it may end up being vaporware. In any case, the act of looking at what's available, listing their strengths and weaknesses and listing the most important features required at CNAG is a valuable exercise in itself.

## Feature Wishlist
* A mechanism for trackng state that doesn't involve creating huge numbers of small files. This pattern causes problems on a filesystem such as lustre which is focussed on large files. Other options could be :
  * A database - prefer postgresql using stored procedures in the database
  * A message / work queue - rabbitmq / celery etc.
  * A distributed key/value store e.g. riak, redis cluster
* A web front end for at least providing stats / tracking information, not necessarily a full gui, possibly using rest api (like arvados)
* Ability to play nicely with dmtcp checkpointing and slurm
* Should be able to understand CWL or WDL, ideally CWL, WDL an Nextflow scripts
* Should place jobs in the batch queue as soon as possible so they get time to accrue priority score based on waiting
* Use of job dependencies in the batch system
