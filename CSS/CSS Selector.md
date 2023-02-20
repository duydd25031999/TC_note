# CSS Selector

Category: CSS
Tags: Basic, Concept

# 1. T****he Cascade****

Recall

- Cascade: thác nước

## Concept

- Thác nước
- If a class is added to that element, apply these styles.
- If element X is a child of element Y, apply those styles.
- Khi thuộc tính của parent được áp dụng cho thằng child (inheritance)

---

# 2. ****Declarations conflict****

## Concept

- 1 style property của 1 element bị nhiều nguồn khác nhau sửa => Declarations conflict

## ****Stylesheet origin****

Where the styles come from.

- Style của element kết hợp giữa code + browser’s default styles
- Origin => cách browser lấy style

### author styles

- style do coder defind
- higher priority

### user agent styles

- browser’s default styles
- lower priority
- với mỗi browser khác nhau thì user agent styles sẽ khác nhau

### important declaration

```css
attribute: value !important
```

- Declarations marked !important are treated as a higher-priority origin
    1. Author important
    2. Author
    3. User agent

---

# 3. ****Selector specificity****

**Recall**

**(!)** Don’t use IDs in your selector.

**(!)** Don’t use !important.

## Questions

[Where is CSS file placed to work with HTML?](Where%20is%20CSS%20file%20placed%20to%20work%20with%20HTML%20ec0477ef67c84852b53773daf80dd5bb.md)

[What is priority of CSS selector and cons of inline style?](What%20is%20priority%20of%20CSS%20selector%20and%20cons%20of%20inlin%201fece2d15fc849d19851641918a5749e.md)

## Concept

- Độ ưu tiên lựa chọn của từng style đối với 1 element

### inline styles

- Inline styles have no selector because they are applied directly to the element they target.
- Nó sẽ bỏ qua các style khác
    - internal style `<style>`
    - external style `<link rel="stylesheet" type="text/css" href="mystyle.css">`
- **(!)** “scoped” declarations
- A selector được chọn bằng cách tính độ specificity
    - • `#id` =higher priority=> `.class` =higher priority=> `tag`
    1. Tính theo `#id` :
        - có #id nhiều hơn sẽ thắng
        - 1 #id =higher priority=> nhiều class
    2. Tính theo `.class` :
        - không có #id thì .class nhiều hơn sẽ thắng
    3. Tính tag : không có #id + .class thì nhiều hơn sẽ thắng

```html
<p class="class1 class2">.class1 .class2</p>
<p id="id1">#id1</p>
<p id="id1" class="class1 class2">#id1 .class1 .class2</p>
```

```css
.class1.class2 {
    color: red;
}
#id1 {
    color: blue; //lấy #id1
}
```

---

```html
<li>
    <a href="/specials" class="featured">
        Specials
    </a>
</li>
```

```css
#main-nav a {   // có #id
    color: white;
    background-color: #13a4a4;
    padding: 5px;
    border-radius: 2px;
    text-decoration: none;
}

.featured {     // ko có #id
    background-color: orange;
}
```

### Source order

- Order in which styles are declared in the stylesheet.
- Thứ tự css được import vào
- **(!)** khi code css thì phải code cho đúng thứ tự

```css
a:link {
    color: blue;
    text-decoration: none;
}

a:visited {
    color: purple;
}

a:hover {
    text-decoration: underline;
}

a:active {
    color: red;
}
```

---

```
-----------------------------      ----------------------------      --------------------      ----------------------      --------------------------
|                           |      |       Different          |      |  Is one an       |      |    Do selectors    |      |    Use declaration     |
|   declarations conflict   |=====>|  origin or importance?   |==NO=>|  inline style?   |==NO=>|    have different  |==NO=>|    that comes later    |
|                           |      |                          |      |  (Scope)         |      |    specificity ?   |      |    in source order     |
-----------------------------      ----------------------------      --------------------      ----------------------      --------------------------
                                                ||                            ||                          ||
                                                YES                           YES                         YES
                                                ||                            ||                          ||
                                                \/                            \/                          \/
                                    ----------------------------      -------------------      ----------------------
                                    |   Use declaration with   |      | Use inline      |      |    Use declaration |
                                    |   higher priority origin |      | declaration     |      |    with higher     |
                                    |                          |      |                 |      |    specificity     |
                                    ----------------------------      -------------------      ----------------------
```

---