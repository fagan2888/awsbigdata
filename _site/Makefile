.PHONY: help book clean serve

help:
	@echo "Please use 'make <target>' where <target> is one of:"
	@echo "  install     to install the necessary dependencies for jupyter-book to build"
	@echo "  book        to convert the `content/` folder into Jekyll markdown in `_build/`"
	@echo "  clean       to clean out site build files"
	@echo "  runall      to run all notebooks in-place, capturing outputs with the notebook"
	@echo "  serve       to serve the repository locally with Jekyll"
	@echo "  build       to build the site HTML locally with Jekyll and store in _site/"


install:
	gem install bundler
	bundle install

list-notebooks:
    #ls *.ipynb | sed -e 's/\.ipynb$//'
book:
	#copy all colab files to lessons
	cp *.ipynb content/lessons/
	jupyter-book build ./

slides:
	# Create slides from notebooks
	jupyter nbconvert content/lessons/*.ipynb --to slides
	mv content/lessons/*.slides.html content/slides

runall:
	jupyter-book run ./content

clean:
	python scripts/clean.py

serve:
	bundle exec guard

site:
	bundle exec jekyll build
	touch _site/.nojekyll
