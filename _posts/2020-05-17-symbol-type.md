---
layout: post
title: The Symbol type in Javascript
---

Discovering many quirks of javascript, symbols being one of them. Functionally, they look like a const string, and can work mostly like a Ruby symbol, which is used to access Object instance variables and hash values.

```ruby
# from rubyguides

    class Food
     attr_accessor :protein
     def initialize(protein)
       @protein = protein
     end
    end

    bacon = Food.new(42)
    bacon.protein
    #-> 42
```

```javascript
// from javascript.info

const id = Symbol("A description")
let user = { name: 'John', [id]: 42 }

user[id]
//-> 42
```

The description will only show up when you use `toString()` on the Symbol, and is not related to accessing it.

However, symbols in JS are default locally scoped, so if the another scope does not have access to the `const id`, code there will not be able to access this property, even if they create another symbol with the same  description. There are ways around that, like `getOwnPropertySymbols()`, but probably has little practical use.

In order to create a Globally scoped Symbol, another syntax must be used.

```javascript
const id = Symbol.for("A description")
```

The same `for()` function is used to both create and access the symbol. Here the description will globally identify this symbol.

As a side note, Typescript will complain if you define a symbol with `let` or `var`, but is fine with `const`. It make sense as you are not suppose to mutate it after creation, but there seems to be no documentation on this.

## Why is it created?

Symbols are unique in that they sit somewhere between a string and an object. Like a string in that they don't have any properties, like an object in that every one is unique. They can help with encapsulation of data within features, and prevent confusion with string conversions.

Unfortunately, the syntax `user[id]` seems quite non-standard, and the not very Object-Oriented nature of JS probably limited its use.
