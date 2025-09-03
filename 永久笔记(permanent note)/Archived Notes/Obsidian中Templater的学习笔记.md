---
creation date: 2024-03-04
tags:
  - Obsidian
type: LearningNote
---
[官方介绍网址](https://silentvoid13.github.io/Templater/)

# A Quick Example 
this example is provided by the author on the official web，let me learn and understand what it exactly do then try to make an our own template
The following template file, that is using [Templater](https://github.com/SilentVoid13/Templater) syntax:


```JavaScript
--- 
creation date: <% tp.file.creation_date() %> 
modification date: <% tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %> 
---  
<< [[<% tp.date.now("YYYY-MM-DD", -1) %>]] | [[<% tp.date.now("YYYY-MM-DD", 1) %>]] >>  
# <% tp.file.title %>  <% tp.web.daily_quote() %>
```


Will produce the following result when inserted:


```JavaScript
--- 
creation date: 2021-01-07 17:20 
modification date: Thursday 7th January 2021 17:20:43 
---  
<< [[2021-04-08]] | [[2021-04-10]] >>  
# Test Test  
> Do the best you can until you know better. Then when you know better, do better. 
> > &mdash; <cite>Maya Angelou</cite>
```

```
//移动笔记文件
<%* await tp.file.move("/我的日记/"+tp.file.title) %>
//笔记文件重命名
<%* await tp.file.rename(tp.file.creation_date("YYYY-MM-DD")+"日记") %>

![[<% await tp.file.find_tfile(tp.file.creation_date("gggg") + "-第" + tp.file.creation_date("ww") + "周").basename %>#本周计划]]
```
---
# Terminology（术语）

To understand how [Templater](https://github.com/SilentVoid13/Templater) works, let's define a few terms:

-   A **template** is a file that contains **[commands](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html./commands/overview.html)**.
-   A text snippet that starts with an opening tag `<%`, ends with a closing tag `%>` is what we will call a **[command](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html./commands/overview.html)**.
-   A **function** is an object that we can invoke inside a **command** and that returns a value (the replacement string)

There are two types of functions you can use:

-   [Internal functions](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html./internal-functions/overview.html). They are **predefined** functions that are built within the plugin. As an example, `tp.date.now` is an internal function that will return the current date.
-   [User functions](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html./user-functions/overview.html). Users can define their own functions. They are either [system command](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html./user-functions/system-user-functions.html) or [user scripts](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html./user-functions/script-user-functions.html).

### [Example](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html#example)

The following template contains 2 commands, calling 2 different internal functions:

```JavaScript
Yesterday: <% tp.date.yesterday("YYYY-MM-DD") %> 
Tomorrow: <% tp.date.tomorrow("YYYY-MM-DD") %>
```

We'll see in the next part the syntax required to write some commands.
# The syntax of Templater(语法规则)
[Templater](https://github.com/SilentVoid13/Templater) uses a custom templating engine ([rusty_engine](https://github.com/SilentVoid13/rusty_engine)) syntax to declare a command. You may need a bit of time to get used to it, but once you get the idea, the syntax is not that hard.

All of Templater's functions are JavaScript objects that are invoked using a **command**.

## Command syntax

A command **must** have both an opening tag `<%` and a closing tag `%>`.

A complete command using the `tp.date.now` internal function would be: `<% tp.date.now() %>`

## Function syntax

### Objects hierarchy

All of Templater's functions, whether it's an internal function or a user function, are available under the `tp` object. You could say that all our functions are children of the `tp` object. To access the "child" of an object, we have to use the dot notation `.`

This means that a Templater function invocation will always start with `tp.<something>`

#### Function invocation
As an example, we would use `tp.date.now()` to invoke the `tp.date.now` internal function.

A function can have arguments and optional arguments. They are placed between the opening and the closing parenthesis, like so:
`tp.date.now(arg1_value, arg2_value, arg3_value, ...)

### Function documentation syntax

The documentation for the internal functions of Templater are using the following syntax:

`tp.<my_function>(arg1_name: type, arg2_name?: type, arg3_name: type = <default_value>, arg4_name: type1|type2, ...)`

Where:
- `arg_name` represents a **symbolic** name for the argument, to understand what it is.
- `type` represents the expected type for the argument. This type must be respected when calling the internal function, or it will throw an error.

1. If an argument is *optional*, it will be appended with a question mark `?`, e.g. `arg2_name?: type`
2. If an argument *has a default value*, it will be specified using an equal sign `=` , `e.g. arg3_name: type = <default_value>`
3. If an argument *can have different types*, it will be specified using a pipe `|`, e.g. `arg4_name: type1|type2`

#### Syntax warning
Please note that this syntax is for documentation purposes only, to be able to understand what arguments the function expects.
You mustn't specify the name nor the type nor the default value of an argument when calling a function. Only the value of the arguments are required, as explained [here](https://silentvoid13.github.io/Templater/syntax.html#function-invocation)

##### Example

Let's take the `tp.date.now` internal function documentation as an example:

`tp.date.now(format: string = "YYYY-MM-DD", offset?: number|string, reference?: string, reference_format?: string)`

This internal function has 4 optional arguments:
- a format of type `string`, with a default value of `"YYYY-MM-DD"`.
- an offset of type `number` or of type `string`.
- a reference of type `string` .
- a reference_format of type `string` .

That means that **valid invocations** for this internal function are:
- `<% tp.date.now() %>`
- `<% tp.date.now("YYYY-MM-DD", 7) %>`
- `<% tp.date.now("YYYY-MM-DD", 7, "2021-04-09", "YYYY-MM-DD") %>`
- `<% tp.date.now("dddd, MMMM Do YYYY", 0, tp.file.title, "YYYY-MM-DD") %>` *Assuming the file name is of the format: "YYYY-MM-DD"

On the other hand, **invalid invocations** are:
- `tp.date.now(format: string = "YYYY-MM-DD")`
- `tp.date.now(format: string = "YYYY-MM-DD", offset?: 0)`
---
# Settings

- You can set a `Template folder location` to tell [Templater](https://github.com/SilentVoid13/Templater) to only check this folder for templates.
- You can set a timeout for your system commands with the `Timeout` option. A system command that takes longer than what you defined will be canceled and considered as a failure.
- You can set [Templater](https://github.com/SilentVoid13/Templater) to be triggered on new file creation. It will listen for the new file creation event and replace every command it finds in the new file's content.

This makes Templater compatible with other plugins like the Daily note core plugin, Calendar plugin, Review plugin, Note refactor plugin, ...

## Security Warning

It can be dangerous if you create new files with unknown / unsafe content on creation. Make sure that every new file's content is safe on creation.

## Folder Templates
You can specify a template that will automatically be used on a selected folder and children using the `Folder Templates` functionality.

**Note**: This setting is hidden by default. To view it first enable the `Trigger Template on new file creation` setting.

## System Commands
You can enable system commands. This allows you to create [user functions](https://silentvoid13.github.io/Templater/user-functions/overview.html) linked to system commands.
### Arbitrary system commands
It can be dangerous to execute arbitrary system commands from untrusted sources. Only run system commands that you understand, from trusted sources.

---
# Internal Functions
The different internal variables and functions offered by [Templater](https://github.com/SilentVoid13/Templater) are available under different **modules**, to sort them. The existing **internal modules** are:
- [Config module](https://silentvoid13.github.io/Templater/internal-functions/internal-modules/config-module.html): `tp.config`
- [Date module](https://silentvoid13.github.io/Templater/internal-functions/internal-modules/date-module.html): `tp.date`
- [File module](https://silentvoid13.github.io/Templater/internal-functions/internal-modules/file-module.html): `tp.file`
- [Frontmatter module](https://silentvoid13.github.io/Templater/internal-functions/internal-modules/frontmatter-module.html): `tp.frontmatter`
- [Hooks module](https://silentvoid13.github.io/Templater/internal-functions/internal-modules/hooks-module.html): `tp.hooks`
- [Obsidian module](https://silentvoid13.github.io/Templater/internal-functions/internal-modules/obsidian-module.html): `tp.obsidian`
- [System module](https://silentvoid13.github.io/Templater/internal-functions/internal-modules/system-module.html): `tp.system`
- [Web module](https://silentvoid13.github.io/Templater/internal-functions/internal-modules/web-module.html): `tp.web`
If you understood the [object hierarchy](https://silentvoid13.github.io/Templater/syntax.html#objects-hierarchy) correctly, this means that a typical internal function call looks like this: `<% tp.<module_name>.<internal_function_name> %>`

---
