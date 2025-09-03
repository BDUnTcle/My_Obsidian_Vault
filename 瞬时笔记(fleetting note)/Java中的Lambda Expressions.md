---
create date: 2024-03-10
modification date: 2024-03-10T21:27:00
tags:
  - 程序员
  - CS/编程语言/Java
  - LambdaExpression
  - "#review"
type: LearningNote
sr-due: 2024-03-31
sr-interval: 3
sr-ease: 250
---
# Basic Concepts
>[!Note] interface in Java
> ```Java
> >public interface Vehicle{
> >		void start();
> >	}
> 
>> public class Car implements Vehicle{
>>	public void start()
>>	{
>>		//do sth...
>>	} 	
>> }
>
>>void startEngine(Vehicle vehicle){
>>	vehicle.start(); //vehicle could be any class inheriente the interface
>>}
> ```

`interface` only provide announcement for method，no implementation，so all method in `interface` is abstract method

---
# Introduction
> [!Question] Why Lambda Expression was introduced ？
> - The tranditional approach to implement a class for a `interface B` is too **complicated**
> 	1. Write a new `Class A` implements `Interface B`
> 	2. In the `Class A`, implement the interface methods
> 	3. Instantiate a `Class A` variable before we use it
>> [!tip] Lambda is used to simplify the procedure above, syntax like this:
>>> ```
>>> interface i = (args...) -> {\\body};
>>>``` 
>>>this statement create a instance of an interface

```Java
//Message.java
public interface Message
{
	void send();
}
//Email.java
Public Email implements Message
{
	void send()
	{
		system.out("This is a email message");
	}
}
//SMS.java
Public SMS implements Message
{
	void send()
	{
		system.out("This is a SMS message");
	}
}
//Main.java
class Main{
	public static void sendMessage(Message message)
	{
		message.send();
	}
	
	public static void main(String[] args)
	{
		Message email = new Email();
		Message sms = new SMS();
		//1. use tranditional way
		sendMessage(email);
		sendMessage(sms);
		
		//2. use Lambda Expression
		sendMessage(() ->{
			system.out("This is a email message");
		});
		sendMessage(() ->{
			system.out("This is a SMS message");
		});
	}
}

```
---
# Constrains
>[!Warning] Lambda Expression can only use when the interface has only 1 method (Functional Interface)

---
# Review List
1. Syntax of lambda expression in Java
2. Functional Interface in Java
---
# Reference
[Java中的Lambda 表达式](https://www.bilibili.com/video/BV1HN4y1C7CQ/?spm_id_from=333.1365.top_right_bar_window_custom_collection.content.click&vd_source=53ab730a6a68286ff34f37d2219cc5d8)