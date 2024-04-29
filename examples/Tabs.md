---
name: "Tabs"
---

# The `tabs` and `tab-content` blocks

The `tabs` block is used to create a tabbed interface. Each tab is defined by a `tab-content` block, which contains the content of the tab, with the list of tabs defined at the beginning of the `tabs` block.

:::: tabs

- [Python](#python)
- [C#](#csharp)
- [JavaScript](#javascript)

::: tab-content | python

```
for i in range(10):
    print(i)
```

:::

::: tab-content | csharp

```csharp
class Program
{
    static void Main(string[] args)
    {
        for (int i = 0; i < 10; i++)
        {
            Console.WriteLine(i);
        }
    }
}
```

:::

::: tab-content | javascript

```javascript
for (let i = 0; i < 10; i++) {
    console.log(i);
}
```

:::

::::