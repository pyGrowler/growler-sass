============
Growler-Sass
============

A Growler_ middleware for rendering sass_ files into CSS.

This implementation uses libsass_ as the backend.

Usage
-----

This package provides the SassMiddleware class exposed in `growler.ext`, as
well as the standard location of `growler_sass`.
This class
To use this,

.. code:: python

    # MUST be called like this! You cannot use import growler.ext.SassMiddleware
    from growler.ext import SassMiddleware
    from growler import App

    app = App("SassExample")

    app.use(SassMiddleware(source="client/style", dest='/styles'))
    ...

    @app.get("/")
    def index(req, res):
       res.send_html("""<!DOCTYPE html>
       <html>
       <head>
         <link href='/styles/neat_style.css' rel='stylesheet'>
         </head>
       <body>
       <p>This text should be red!</p>
       </body>
       </html>""")

    app.create_server_and_run_forever()

.. _Growler: https://github.com/pyGrowler/Growler
.. _sass: http://www.makotemplates.org/
.. _libsass: https://hongminhee.org/libsass-python/
