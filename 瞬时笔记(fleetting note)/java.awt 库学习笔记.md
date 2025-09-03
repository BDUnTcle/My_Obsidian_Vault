#CS/编程语言/Java #程序员 #CS/编程语言 #GUI 

## java.awt.event
### ActionListener/ActionPublisher
Controls (JButton, JTextField, JMenuItem, etc.) publish action events when selected/clicked/touched/etc. Programmer-defined controllers implement the ActionListener interface and subscribe to any controls they are interested in. When that control fires an action event, the controller's implementation of actionPerformed is automatically called. This method typically updates the application's model in some way.
**one application of iPublisher-Subscriber pattern**
![[Pasted image 20240225093215.png|600]]

```java
//Create a Button and subscribe
JPanel p = new JPanel();  
JButton change = new JButton("Parse");   
change.addActionListener(Jpanel.this);

```
