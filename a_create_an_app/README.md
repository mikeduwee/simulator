# a. Create an app

## minimal app
First off, let’s get familiar with the Kivy app life cycle.
<img src="https://kivy.org/doc/stable/_images/Kivy_App_Life_Cycle.png">

As you can see above, for all intents and purposes, our entry point into our App is the run() method, and in our case that is “MyApp().run()”. We will get back to this, but let’s start from the third line:

from kivy.app import App

It’s required that the base Class of your App inherits from the App class. It’s present in the kivy_installation_dir/kivy/app.py.

Note

Go ahead and open up that file if you want to delve deeper into what the Kivy App class does. We encourage you to open the code and read through it. Kivy is based on Python and uses Sphinx for documentation, so the documentation for each class is in the actual file.

Similarly on line 2:

from kivy.uix.label import Label

One important thing to note here is the way packages/classes are laid out. The uix module is the section that holds the user interface elements like layouts and widgets.

Moving on to line 5:

class MyApp(App):

This is where we are defining the Base Class of our Kivy App. You should only ever need to change the name of your app MyApp in this line.

Further on to line 7:

def build(self):

As highlighted by the image above, show casing the Kivy App Life Cycle, this is the function where you should initialize and return your Root Widget. This is what we do on line 8:

return Label(text='Hello world')

Here we initialize a Label with text ‘Hello World’ and return its instance. This Label will be the Root Widget of this App.

Note

Python uses indentation to denote code blocks, therefore take note that in the code provided above, at line 9 the class and function definition ends.

Now on to the portion that will make our app run at line 11 and 12:

if __name__ == '__main__':
    MyApp().run()

Here the class MyApp is initialized and its run() method called. This initializes and starts our Kivy application.

## my_second_app

Lets extend this application a bit, say a simple UserName/Password page.

At line 2 we import a Gridlayout:

from kivy.uix.gridlayout import GridLayout

This class is used as a Base for our Root Widget (LoginScreen) defined at line 9:

class LoginScreen(GridLayout):

At line 12 in the class LoginScreen, we override the method __init__() so as to add widgets and to define their behavior:

def __init__(self, **kwargs):
    super(LoginScreen, self).__init__(**kwargs)

One should not forget to call super in order to implement the functionality of the original class being overloaded. Also note that it is good practice not to omit the **kwargs while calling super, as they are sometimes used internally.

Moving on to Line 15 and beyond:

self.cols = 2
self.add_widget(Label(text='User Name'))
self.username = TextInput(multiline=False)
self.add_widget(self.username)
self.add_widget(Label(text='password'))
self.password = TextInput(password=True, multiline=False)
self.add_widget(self.password)

We ask the GridLayout to manage its children in two columns and add a Label and a TextInput for the username and password.

Running the above code will give you a window that should look like this:
<img src="https://kivy.org/doc/stable/_images/guide_customize_step1.png">
Try re-sizing the window and you will see that the widgets on screen adjust themselves according to the size of the window without you having to do anything. This is because widgets use size hinting by default.

The code above doesn’t handle the input from the user, does no validation or anything else. We will delve deeper into this and Widget size and positioning in the coming sections.
