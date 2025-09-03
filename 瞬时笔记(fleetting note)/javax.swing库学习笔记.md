#CS/编程语言/Java #程序员 #CS/编程语言 #GUI

## JFrame 类
If you want to design and show a window, you need to instantiate a JFrame with some default callings
```java
		// add frame and run:
        frame = new JFrame();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setTitle("Blank App");
        frame.setSize(500, 300);
        frame.setVisible(true);
```

# JComponent
## JPanel类
Subclass of *JComponent* 。 A desttop window is a *Jpanel* surrounded by a *JFrame*
Use JPanel could create a GUI container
Also see [[java.awt 库学习笔记#ActionListener/ActionPublisher]]
```Java
public class AppPanel extends JPanel implements ActionListener {

    public AppPanel() {

        // add controls and sub-panels here

        // add frame and run:
        frame = new JFrame();
        Container cp = frame.getContentPane();
        cp.add(this);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setTitle("Blank App");
        frame.setSize(500, 300);
        frame.setVisible(true);
    }

    public void actionPerformed(ActionEvent ae) {
        // react to user input here
    }


    public static void main(String[] args) {
        AppPanel app = new AppPanel();
    }

}

```
### LayoutManager
Using different layout to set the layout stratege
![[Pasted image 20240225100536.png|600]]
```java
controls = new ControlPanel();  
this.setLayout((new GridLayout(1, 2)));  
this.add(controls);
```
---
## JMenu，JMenuItem， JMenuBar
to implement a Menubar of your app

```java
JFrame frame = new JFrame();
frame.setJMenuBar(this.createMenuBar());

public static JMenu makeMenu(String name, String[] items, ActionListener handler) {  
    JMenu result = new JMenu(name);  
    for(int i = 0; i < items.length; i++) {  
        JMenuItem item = new JMenuItem(items[i]);  
        item.addActionListener(handler);  
        result.add(item);  
    }  
    return result;  
}

protected JMenuBar createMenuBar() {  
    JMenuBar result = new JMenuBar();  
    JMenu fileMenu = Utilities.makeMenu("File", new String[]{"New", "Save", "Open", "Quit"}, this);  
    result.add(fileMenu);  
    JMenu editMenu = Utilities.makeMenu("Edit", new String[]{"Change"}, this);  
    result.add(editMenu);  
    JMenu helpMenu = Utilities.makeMenu("Help", new String[]{"About", "Help"}, this);  
    result.add(helpMenu);  
    return result;  
}
```
---
## JOptionPane
`JOptionPane` makes it easy to pop up a standard dialog box that prompts users for a value or informs them of something.

```java
public static boolean confirm(String query) {  
    int result = JOptionPane.showConfirmDialog(null,  
            query, "choose one", JOptionPane.YES_NO_OPTION);  
    return result == 0;  
}  
  
// asks user for info  
public static String ask(String query) {  
    return JOptionPane.showInputDialog(null, query);  
}  
  
// tells user some info  
public static void inform(String info) {  
    JOptionPane.showMessageDialog(null,info);  
}
// tells user about an error  
public static void error(String gripe) {  
    JOptionPane.showMessageDialog(null,  
            gripe,  
            "OOPS!",  
            JOptionPane.ERROR_MESSAGE);  
}
```

---
# Border
Provides classes and interface for drawing specialized borders around a Swing component. You can subclass these classes to create customized borders for your components instead of using the default borders provided by the look-and-feel being used.

```java
Border blackline = BorderFactory.createLineBorder(Color.black);  
setBorder(blackline);  
setBackground(Color.LIGHT_GRAY);
```
