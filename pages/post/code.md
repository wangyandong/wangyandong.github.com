title: test for code hilight
date: 2013-08-03

	from flask import Flask, render_template
	from flaskext.flatpages import FlatPages

	DEBUG = True
	FLATPAGES_AUTO_RELOAD = DEBUG
	FLATPAGES_EXTENSION = '.md'

	app = Flask(__name__)
	app.config.from_object(__name__)
	pages = FlatPages(app)

	@app.route('/')
	def index():
	    return "Hello World"

	@app.route('/<path:path>/')
	def page(path):
	    page = pages.get_or_404(path)
	    return render_template('page.html', page=page)

	if __name__ == '__main__':
	    app.run(port=8000)

