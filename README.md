Binboy's Tech Blog 
---------------------

This is my tech blog using Jupyter notebooks.

Run the blog locally
---------------------

You can reproduce this setup on your own computer by following the steps below:

* Create a virtualenv.
* Install everything in `requirements.txt`.
* Setup your `.gitignore` file.
* Run `pelican-quickstart`.
* Create a `plugins` folder.
* Run `git init`.
* Run `git submodule add git://github.com/danielfrg/pelican-ipynb.git plugins/ipynb`.
* Create any notebooks you want in the `content` folder.
    * Remember to create corresponding `.ipynb-meta` files.
    * Remember to create a meta header if using markdown in a `.md` file.
* Edit pelicanconf.py to the lines that activate the `pelican-ipynb` plugin.
* Run `pelican content`.
* Switch to the `output` directory and run `python -m pelican.server`.
* Open `http://localhost:8000/` to preview.

Deploy to GitHub Pages
---------------------

* Run `ghp-import output -b master` to import everything in the output folder to the master branch.
* Use `git push origin master` to push your content to Github.
* Try visiting `https://binlogo.github.io/`.

More Info
--------

See [this](https://www.dataquest.io/blog/how-to-setup-a-data-science-blog/) blog post for more details, and a guide on how to setup and deploy a blog.