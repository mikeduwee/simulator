# simulator

## 0_Installing kiwi in linux
Wheels are precompiled binaries for all linux platforms using the manylinux2010 tag. In the following, replace python with python3 for Python 3. To install first update pip:

`$ python -m pip install --upgrade --user pip setuptools virtualenv`

Then make and load the virtualenv. This is optional, but highly recommended:

`$ python -m virtualenv ~/kivy_venv`
`$ source ~/kivy_venv/bin/activate`

Finally install the Kivy wheel and optionally the kivy-examples:

`$ python -m pip install kivy`
`$ python -m pip install kivy_examples`

Gstreamer is not included, so if you would like to use media playback with kivy, you should install ffpyplayer like so

`$ python -m pip install ffpyplayer`

Make sure to set KIVY_VIDEO=ffpyplayer env variable before running the app. Only Python 3.5+ is supported.
Nightly wheel installation¶

Warning
Using the latest development version can be risky and you might encounter issues during development. If you encounter any bugs, please report them.

## a) create an app
[create an app documentation](a_create_an_app/README.md)