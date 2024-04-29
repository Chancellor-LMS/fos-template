---
name: "Code with Syntax Highlighting"
---

# Code Blocks

Code blocks are enclosed in triple backticks (```) and are used to display code snippets. You can specify the language for syntax highlighting.

````markdown
```python
def hello_world():
    print("Hello, World!")
```
````

Produces:

```python
def hello_world():
    print("Hello, World!")
```

And

````markdown
```javascript
function helloWorld() {
    console.log("Hello, World!");
}
```
````

Produces:

```javascript
function helloWorld() {
    console.log("Hello, World!");
}
```

# Code files custom block

A `codefile` (included in the template) block is available to add a file name to the code block.

````markdown
::: codefile | Project/Program.cs
```csharp
using System;
namespace HelloWorld
{
    class Program
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```
:::
````

Produces:

::: codefile | Project/Program.cs
```csharp
using System;
namespace HelloWorld
{
    class Program
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```
:::

# Custom Syntax Highlighting

Different styling can be applied by updating the `code-github-dark.css` file in the `.chancellor` folder. The template uses [`github-dark`](https://github.com/highlightjs/highlight.js/blob/main/src/styles/github-dark.css) as the default style.

You may update the CSS classes for different tokens, or browse [highlight.js](https://github.com/highlightjs/highlight.js/tree/main/src/styles) for examples by selecting a style and copying the content to the `code-github-dark.css` file.