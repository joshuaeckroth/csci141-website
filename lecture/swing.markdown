---
title: Swing
layout: default
---

## Frames

```
public static void gui() {
	JFrame frame = new JFrame("My Frame!");
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    frame.setSize(250,250);
    frame.pack();
    frame.setVisible(true);
}

public static void main(String[] args)
{
	SwingUtilities.invokeLater(new Runnable() {
        public void run() {
            gui();
        }
    });
}
```

## Panels and layouts

![Java layouts](/images/java-layouts.gif)

Image from [Java Foundation Classes in a Nutshell](http://docstore.mik.ua/orelly/java-ent/jfc/ch02_05.htm). More examples: [A visual guide to layout managers](https://docs.oracle.com/javase/tutorial/uiswing/layout/visual.html).

### BorderLayout

![BorderLayout](/images/border-layout.png)

Image from [Wikipedia](http://commons.wikimedia.org/wiki/File:Java-LayoutManager-BorderLayout.svg).

```

JPanel win = new JPanel(); // or JFrame
win.setLayout(new BorderLayout());
// use NORTH or SOUTH or EAST or WEST or CENTER
win.add(myLabel, BorderLayout.NORTH);
```

### FlowLayout

![FlowLayout](/images/flow-layout.gif)

Image from [zentut](http://www.zentut.com/java-swing/java-swing-flowlayout/).

```
JButton component1 = new JButton();
JButton component2 = new JButton();
JPanel panel = new JPanel(new FlowLayout(FlowLayout.CENTER)); // or LEFT or RIGHT
panel.add(component1);
panel.add(component2);
```

### GridLayout

![GridLayout](/images/grid-layout.gif)

Image from [zentut](http://www.zentut.com/java-swing/java-swing-gridlayout/).

```
JButton btn1 = new JButton("Button 1");
JButton btn2 = new JButton("Button 2");
JButton btn3 = new JButton("Button 3");
JButton btn4 = new JButton("Button 4");
JButton btn5 = new JButton("Button 5");
// create grid layout with 3 rows , 2 columns with horizontal
// and vertical gap set to 10
JPanel panel = new JPanel(new GridLayout(3, 2, 10, 10));
// add buttons to the panel
panel.add(btn1);
panel.add(btn2);
panel.add(btn3);
panel.add(btn4);
panel.add(btn5);
```

### GridBagLayout

![GridBagLayout](/images/grid-bag-layout.png)

Image from [Java2s.com](http://www.java2s.com/Tutorial/Java/0240__Swing/UsingGridBagConstraints.htm).

```
frame.setLayout(new GridBagLayout());
JButton button;
// Row One - Three Buttons
button = new JButton("One");
addComponent(frame, button, 0, 0, 1, 1, GridBagConstraints.CENTER, GridBagConstraints.BOTH);
button = new JButton("Two");
addComponent(frame, button, 1, 0, 1, 1, GridBagConstraints.CENTER, GridBagConstraints.BOTH);
button = new JButton("Three");
addComponent(frame, button, 2, 0, 1, 1, GridBagConstraints.CENTER, GridBagConstraints.BOTH);
// Row Two - Two Buttons
button = new JButton("Four");
addComponent(frame, button, 0, 1, 2, 1, GridBagConstraints.CENTER, GridBagConstraints.BOTH);
button = new JButton("Five");
addComponent(frame, button, 2, 1, 1, 2, GridBagConstraints.CENTER, GridBagConstraints.BOTH);
// Row Three - Two Buttons
button = new JButton("Six");
addComponent(frame, button, 0, 2, 1, 1, GridBagConstraints.CENTER, GridBagConstraints.BOTH);
button = new JButton("Seven");
addComponent(frame, button, 1, 2, 1, 1, GridBagConstraints.CENTER, GridBagConstraints.BOTH);
```

The code above uses a helper function (which you must include if you want to use the `addComponent` method as above):

```
private static final Insets insets = new Insets(0, 0, 0, 0);
private static void addComponent(
       Container container, Component component,
       int gridx, int gridy, int gridwidth, int gridheight,
       int anchor, int fill) {
       
    GridBagConstraints gbc = new GridBagConstraints(gridx, gridy, gridwidth, gridheight,
        1.0, 1.0, anchor, fill, insets, 0, 0);
        
    container.add(component, gbc);
  }
```

### Box layout (vertical/horizontal layouts)

```
Box box = new Box(BoxLayout.Y_AXIS); // or X_AXIS
JButton b1 = new JButton("1");
JButton b2 = new JButton("2");
JButton b3 = new JButton("3");
box.add(b1);
box.add(b2);
box.add(b3);
```


## Labels

```
JLabel myLabel = new JLabel();
myLabel.setText("foo bar");
```

Or,

```
JLabel myLabel = new JLabel("foo bar");
```

## Buttons

```
JButton myButton = new JButton();
myButton.setText("foo bar");
```

Or,

```
JButton myButton = new JButton("foo bar");
```

You can use an icon for the button:

```
JButton b1 = new JButton(new ImageIcon("filename.png"));
// or:
JButton b2 = new JButton();
b2.setIcon(new ImageIcon("filename.png"));
```

## Events

When a button is clicked, or text is entered into a text box, and so on, events are fired. Unless you do something special, these events are ignored by your program. But you can instead choose to "listen" to certain events and respond to them. For example, you may want something to happen when a certain button is clicked.

To create an event listener, you need to create a class that `implements` the `ActionListener` interface, which requires that your class has a method called `actionPerformed(ActionEvent e)`. (You don't have to name your parameter `e` but we usually do.)

Recall from the [Interfaces](/lecture/interfaces.html) notes that you can create an anonymous class instance that implements an interface. So, you can create a listener like this:

```
new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        System.out.println("I'm responding to an event!");
    }
}
```

You'd usually put that kind of code in an `addActionListener` on a button or other object:

```
JButton myButton = new JButton();
myButton.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        System.out.println("I'm responding to an event!");
    }
});
```

## Custom drawing

Do you wish to draw arbitrary rectangles, ellipses (now called "ovals"), etc.?

First, you need to make a class that's a subclass of `JPanel`:

```
public class MyPanel extends JPanel {

}
```

Then you need to override two methods:

```
public Dimension getPreferredSize() {
    return new Dimension(500, 250); // add your panel's preferred size
}

public void paintComponent(Graphics g) {
    super.paintComponent(g);
    
    // draw your own stuff
}
```

Then make a new instance of your panel and add it to some layout:

```
JFrame myFrame = new JFrame();
MyPanel myPanel = new MyPanel();
myFrame.add(myPanel);
```

Within your overridden `paintComponent` method, you can call various drawing operations on the `g` object:

```
g.setColor(Color.yellow);
g.drawRect(x, y, 20, 20);
g.fillRect(x, y, 10, 10);
g.fillOval(x, y, 5, 10);
```

And so on. Look at [this tutorial](http://docs.oracle.com/javase/tutorial/2d/geometry/index.html) for more drawing methods, and [this tutorial](http://docs.oracle.com/javase/tutorial/2d/index.html) for a larger view of 2D graphics in Java.

## Tables

Create a table with initial content.

```
String[][] data = { {"John", "Doe", "3.5"}, {"Jane", "Smith", "3.9"} };
String[] colNames = {"Firstname", "Lastname", "GPA"};
DefaultTableModel model = new DefaultTableModel(data, colNames);
JTable mytable = new JTable(model);
myframe.add(new JScrollPane(mytable), BorderLayout.WEST);
```

Add a row.

```
String[] vals = {"(unknown)", "(unknown)", "(unknown)"};
model.addRow(vals);
```

Delete the selected row (if a row is selected).

```
int row = mytable.getSelectedRow();
if(row != -1) { model.removeRow(row); }
```

## File open/save dialogs

```
FileDialog diag = new FileDialog(myframe, "Open File", FileDialog.LOAD); // or FileDialog.SAVE
diag.setVisible(true);
if(diag.getFiles().length > 0) {
    System.out.println(diag.getFiles()[0].getAbsolutePath());
}
```
