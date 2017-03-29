## Genreal Concepts

### Cascade & Inheritance
The cascade algorithm determines which CSS rules will be applied to an element. For determination, three factors are significant:

1. Importance
2. Specificity
3. Source order

#### Importance
To keep this short: If a CSS rule has applied `!important` to it, it will win in almost all cases. 

```html
  <a id="button" href="#">Buy now</a>
```

```css
/* A very specific rule */
#button {
  background-color: green;
}

/* This will win anyway */
a {
  background-color: red; !important
}
```

A good rule of thumb is to **never use `!important`**.  
There are some exceptions where `!important` can be overridden:

  
There are some exceptions where `!important` can be overridden:

1. When a second `!important` statement is placed later in the code 
2. When another stylesheet with a higher priority overrides the rule

#### Specificity
Rules are ordered by specificity, the rule with the highest specificity is applied. To rank the specificity of a rule, a point system is applied.

Type | Points
--- | ---
Inside a `<style>` tag or inline styles | 1000s
`#IDs` | 100s
`.classes`, attribute-selectors (`a[href="home"]`) or `:pseudo-classes` | 10s
Element selectors | 1s

These numbers are added, so a rule like

```css
#button .primary a:hover {
  color: green'
}
```

would have a score of 121.

#### Source Order
Simply put: Later rules in the stylesheet override earlier ones *with the same score*.

Also, different stylesheets have different priorities. For example, the author stylesheet has a higher priority than the user agent stylesheet (that's the reason CSS resets can exist).

Rank | Origin | Importance
--- | --- | ---
1 | user agent | normal
2 | user | normal
3 | author | normal
4 | CSS Animations | it's complicated
5 | author | `!important`
6 | user | `!important`
7 | user-agent | `!important`

(A higher rank means higher priority)

#### Further Reading
* [](https://developer.mozilla.org/en-US/docs/Web/CSS/Cascade)
* [](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance)
