# Experimenting with Mediawiki API and network graphs

[![nbviewer](https://raw.githubusercontent.com/jupyter/design/master/logos/Badges/nbviewer_badge.svg)](https://nbviewer.jupyter.org/github/UncleCJ/pywikibot-gephi-experiments/blob/dev3/pywikibot2gephi.ipynb) [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/UncleCJ/pywikibot-gephi-experiments/dev3?filepath=pywikibot2gephi.ipynb)

This README is included in the [pywikibot2gephi.ipynb Jupyter notebook](pywikibot2gephi.ipynb), you might as well head right over there.

## TL;DR;

> These are my experiments in learning how to use any Mediawiki API through Pywikibot to collect any data I am interested in processing as a network graph (originally in convenient tool Gephi). Besides pretty pictures, network graphs offer powerful methods to visualize and elucidate data in ways which would be difficult otherwise. Two applications I have in mind are are [story narrative charts](https://xkcd.com/657) and as aid in corporate wiki management.


## Overview

For [the longest time](http://unclecj.blogspot.com/search/label/gephi), I've enjoyed playing with various types of network graphs, mainly using the revered open source tool [Gephi](https://github.com/gephi/gephi). However, data acquisition and preparation is usually the challenge, so I've been wanting to get into programmatic ways of working with the data. I haven't so far explored... lower-level tools like [neo4j](https://neo4j.com) or [Wikibase](https://wikiba.se) (together with [Mediawiki](https://www.mediawiki.org/wiki/MediaWiki) the software powering [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page), itself the structured data storage behind [Wikipedia](https://www.wikipedia.org/)).

From the beginning, I've usually fed Gephi by creating some type of CSV/spreadsheet [node-, edge lists or adjacency matrix](https://gephi.org/users/supported-graph-formats/csv-format/). With some learning effort and assuming your data is in for instance Wikidata, you can feed it from the [SemanticWebImport Gephi plugin](https://github.com/gephi/gephi/wiki/SemanticWebImport) and SPARQL queries (see my [previous tutorial on that](https://gist.github.com/UncleCJ/2408aef8eab09cc1da3404c5af43537b)). There is also the option to simply [scrape the web](https://medium.com/@dakarabas/how-to-easily-visualize-your-internal-links-with-python-4467ef1e8c4d) (that example using [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/), [Selenium](https://www.selenium.dev), [Pandas](https://github.com/pandas-dev/pandas), [NetworkX](https://github.com/networkx/networkx) and [Matplotlib](https://github.com/matplotlib/matplotlib)), but that can easily get messy.

Thus follows my current toolchain - there are lots of exciting data accessible through the [Mediawiki APIs](https://www.mediawiki.org/wiki/API:Main_page) (not only Wikipedia but also sites in the [Fandom/Wikia family](https://en.wikipedia.org/wiki/Fandom_(website)) or perhaps your corporate wiki?). [Pywikibot](https://github.com/wikimedia/pywikibot) offers a convenient and well-used (though not as well documented?) Python wrapping for Mediawiki API, such as authentication, parsing, caching and configurable throttling. [igraph](https://github.com/igraph/python-igraph) (n.b. `python-igraph`) seems sensible and provides an interface to the [Gephi GraphStreaming plugin](https://github.com/gephi/gephi/wiki/GraphStreaming). Jupyter notebooks are practically a given (see also my [advent-of-code solutions](https://github.com/UncleCJ/advent-of-code), also in Jupyter notebooks)

As for potential paths of development, for when you don't have Gephi running along the notebook, [one could opt for NetworkX](https://www.reddit.com/r/Python/comments/4g9lp0/comment/d2i0r45/?utm_source=share&utm_medium=web2x&context=3) as well as further usage of [IPython.display](https://ipython.readthedocs.io/en/stable/api/generated/IPython.display.html), or even trying out something like [pyvis](https://github.com/WestHealth/pyvis) (article [here](https://towardsdatascience.com/pyvis-visualize-interactive-network-graphs-in-python-77e059791f01), see also their [two](https://towardsdatascience.com/visualising-graph-data-with-python-igraph-b3cc81a495cf) previous [articles](https://towardsdatascience.com/newbies-guide-to-python-igraph-4e51689c35b4)).

Wikimedians may expect [more Wikidata](https://www.wikidata.org/wiki/Wikidata:Pywikibot_-_Python_3_Tutorial) or even [PAWS](https://wikitech.wikimedia.org/wiki/PAWS), but that's not where I'm going currently.

For inspiration, I draw mainly on [Aidan Hogan](https://github.com/aidhog) et al. article "[Knowledge Graphs (extended version)](https://aidanhogan.com)" and [Alberto Cottica](https://github.com/albertocottica) et al. presentation "[People, words, data: Harvesting collective intelligence](https://edgeryders.eu/t/internet-of-humans-matchmaking-event-in-stockholm/9705/81?u=unclecj)" and article "[Semantic Social Networks: A Mixed Methods Approach to Digital Ethnography](https://journals.sagepub.com/doi/10.1177/1525822X20908236)"

## Usage


* Have [Python 3.x](https://www.python.org/downloads) with [Jupyter](https://pypi.org/project/jupyter) and preferably something like [virtualenv](https://pypi.org/project/virtualenv) installed
* Define a virtualenv or similar to keep dependencies managable for this project: `virtualenv ./venv` . Activate it like `source venv/bin/activate`. In it, `pip install -r requirements.txt`
* IDEs like [VS Code](https://code.visualstudio.com/docs/python/environments) may pick up on your virtualenv, or you may have to [register it with IPython](https://www.janmeppe.com/blog/how-to-add-new-kernel-in-jupyter-notebook)
* Open the notebook in your IDE, or through Jupyter: `jupyter pywikibot2gephi.ipynb`
* _Optionally, install [Gephi (0.9.2)](https://gephi.org/users/download), start it and activate the [Graph Streaming](https://gephi.org/plugins/#/plugin/graphstreaming) "master server"_
* Run, explore and modify the examples!

Alternatively, just click the ["launch binder" button](https://mybinder.org/v2/gh/UncleCJ/pywikibot-gephi-experiments/dev2?filepath=pywikibot2gephi.ipynb) and [mybinder.org](https://mybinder.org/) together with [repo2docker GitHub Actions](https://discourse.jupyter.org/t/how-to-reduce-mybinder-org-repository-startup-time/4956/2) should have all the requirements sorted for you in a jiffy (obviously a binder won't be able to connect to a local Gephi). Another option is to install the notebook in [PAWS: A Web Shell (PAWS)](https://wikitech.wikimedia.org/wiki/PAWS), but I haven't tried that.


## Changelog

### 2021-10-16

Cleaned up the project, wrote down (and reconstructed) this README. Currently working in the `dev3` branch, because of how I want things tidy before I set them in stone (a.k.a. `main`)
### 2021-10-10

Created this repository and started my experiments. Yesterday I confirmed that by hard-coding our corporate SSO session cookie (figure out a way to pull it from the browser?) in [`pywikibot.lwp`](https://github.com/wikimedia/pywikibot/blob/master/pywikibot/comms/http.py) ("[Set-Cookie3 format](https://docs.python.org/2/library/cookielib.html#filecookiejar-subclasses-and-co-operation-with-web-browsers)"), the regular MediaWiki API of the corporate wiki is usable. So while this is playing around for personal education, my hope is it could be quite useful also for various methods of corporate information- and community management


## See also

* https://public.paws.wmcloud.org/309423/ds4ux/jupyter-intro.ipynb
* https://public.paws.wmcloud.org/19781798/WikidataMapMakingWorkshop/WikidataMapMakingWorkshop.ipynb
* https://pythonrepo.com/repo/markusschanta-awesome-jupyter-python-repl
* https://heardlibrary.github.io/digital-scholarship/host/wikidata/bot/
* https://heardlibrary.github.io/digital-scholarship/host/wikidata/pywikibot/
* https://cambridge-intelligence.com/python-graph-visualization-using-jupyter-regraph/
* http://compbio.ucsd.edu/bringing-interactivity-network-visualization-jupyter-notebooks-visjs2jupyter/
* https://ipython-books.github.io/64-visualizing-a-networkx-graph-in-the-notebook-with-d3js/
* https://melaniewalsh.github.io/Intro-Cultural-Analytics/06-Network-Analysis/02-Making-Network-Viz-with-Bokeh.html
* https://github.com/adamhajari/nbgitconvert
* https://medium.com/@mjspeck/presenting-code-using-jupyter-notebook-slides-a8a3c3b59d67
* https://www.blog.pythonlibrary.org/2018/09/25/creating-presentations-with-jupyter-notebook/
