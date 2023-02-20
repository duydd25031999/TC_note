# HtmlElement

Category: Javascript
Tags: Concept, Low

# Attribute

### accessKey

- Key để access vào element

### hidden

- Boolean: element is hidden or note

### innerText

- String: only text in content

### offsetWidth

- Number (px)

= margin + border + padding + content

= margin + clientWidth

### offsetHeight

- Number (px)

= margin + border + padding + content

= margin + clientHeight

### offsetLeft

- Number (px)
- css `left`

### offsetTop

- Number (px)
- css `top`

## **Event handlers**

- onXYZ ⇒ Event listeners cho event XYZ

## Methods

- `.XYZ()` ⇒ trigger event

## **Element**

### classList

- List class
- Read only
- Không phải class
- `.remove(className)` : bỏ class
- `.add(className)` : thêm class
- `.contains(className)` : check contains class
- `.replace(oldClass, newClass)` : replate class

### clientWidth

= border + padding + content

- Read only
- Number (px)

### clientHeight

= border + padding + content

- Read only
- Number (px)

### clientLeft

= border-left-width

- Read only
- Number (px)

### clientTop

= border-top-width

- Read only
- Number (px)

### id

- Attribute id of Element

### innerHtml

- String
- Content html

### outerHTML

- String
- Current html + innerHtml

### scrollHeight

= padding + content (all height - overflow)

- Read only
- Number (px)

### scrollWidth

= padding + content (all width - overflow)

- Read only
- Number (px)

### scrollTop

- Tung độ content được scroll tới
- Number (px)

### scrollLeft

- Hoành độ content được scroll tới
- Number (px)

## HTMLCollection

- Return từ `getElementsByClassName`, `getElementsByTagName`
- Không phải 100% Array
    
    ⇒ không dùng 100% method của array được
    
    - Dùng `Array.from(htmlCollection)` ⇒ HtmlElement[]
    
    ⇒ Dùng hết các method của array
    

## NodeList

- Return từ `querySelectorAll`

---