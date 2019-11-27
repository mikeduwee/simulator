# pong game tutorial

## Add Simple Graphics
Explaining the Kv File Syntax

Before going on to the next step, you might want to take a closer look at the contents of the kv file we just created and figure out what is going on. If you understand what’s happening, you can probably skip ahead to the next step.

On the very first line we have:

`#:kivy 1.11.1`

This first line is required in every kv file. It should start with #:kivy followed by a space and the Kivy version it is intended for (so Kivy can make sure you have at least the required version, or handle backwards compatibility later on).

After that, we begin defining rules that are applied to all PongGame instances:

`<PongGame>:
    ...
`

Like Python, kv files use indentation to define nested blocks. A block defined with a class name inside the < and > characters is a Widget rule. It will be applied to any instance of the named class. If you replaced PongGame with Widget in our example, all Widget instances would have the vertical line and the two Label widgets inside them because it would define these rules for all Widget instances.

Inside a rule section, you can add various blocks to define the style and contents of the widgets they will be applied to. You can:

  - set property values,
  -  add child widgets
  -  define a canvas section in which you can add Graphics instructions that define how the widget is rendered.

The first block inside the <PongGame> rule we have is a canvas block:

`
<PongGame>:
    canvas:
        Rectangle:
            pos: self.center_x - 5, 0
            size: 10, self.height
`

So this canvas block says that the PongGame widget should draw some graphics primitives. In this case, we add a rectangle to the canvas. We set the pos of the rectangle to be 5 pixels left of the horizontal center of the widget, and 0 for y. The size of the rectangle is set to 10 pixels in width, and the widget’s height in height. The nice thing about defining the graphics like this, is that the rendered rectangle will be automatically updated when the properties of any widgets used in the value expression change.

Note

Try to resize the application window and notice what happens. That’s right, the entire UI resizes automatically. The standard behaviour of the Window is to resize an element based on its property size_hint. The default widget size_hint is (1,1), meaning it will be stretched 100% in both x-direction and y-direction and hence fill the available space. Since the pos and size of the rectangle and center_x and top of the score labels were defined within the context of the PongGame class, these properties will automatically update when the corresponding widget properties change. Using the Kv language gives you automatic property binding. :)

The last two sections we add look pretty similar. Each of them adds a Label widget as a child widget to the PongGame widget. For now, the text on both of them is just set to “0”. We’ll hook that up to the actual score once we have the logic implemented, but the labels already look good since we set a bigger font_size, and positioned them relatively to the root widget. The root keyword can be used inside the child block to refer back to the parent/root widget the rule applies to (PongGame in this case):

<PongGame>:
    # ...

    Label:
        font_size: 70
        center_x: root.width / 4
        top: root.top - 50
        text: "0"

    Label:
        font_size: 70
        center_x: root.width * 3 / 4
        top: root.top - 50
        text: "0"

