# The Symbol type in Javascript

`2020-05-17`

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

#### Why is it created?

Symbols are unique in that they sit somewhere between a string and an object. Like a string in that they don't have any properties, like an object in that every one is unique. They can help with encapsulation of data within features, and prevent confusion with string conversions.

Unfortunately, the syntax `user[id]` seems quite non-standard, and the not very Object-Oriented nature of JS probably limited its use.

# Wiping Free Space

`2020-05-18`

Wiping the free space of a drive is useful when the drive is not encrypted, and you want to make sure deleted files cannot be recovered. Wiping multiple times is mostly useless now, as the original analysis by Peter Gutmann, which found that expensive equipment can sometimes detect the original value of an overwritten bit, was done on obsolete hardware, whereas modern harddisks are made with much higher densities and tighter tolerances. Filling all empty space with 0s will most likely be enough.

It is important to note that this is not a fault-prove method, as there may still be data left in relocated or bad sectors. Physical destruction or full disk encryption would be the preferred method for better security.

Windows:

```
cipher /w:C:\
```

Linux:

```bash
cat /dev/zero > zero.file
sync
rm zero.file
```
