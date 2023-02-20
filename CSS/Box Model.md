# Box Model

<!--- TODO: UPDATE -->

- Table of content

# 1. ****box-sizing****

## Questions

[What is border-box?](https://www.notion.so/What-is-border-box-daf33bb229914eb89e5bca6cd73a4983)

## content-box

- "width" và "height" chỉ để định nghĩa content size.
- Border và padding không included
- **(!)** Default border-box
- "width" x "height" = content + border + padding

---

# 2. S****horthand values****

**Notes**

- dùng cho padding, margin
    - top, right, bottom, left
    - top, right & left, bottom
    - horizonal, vertical
        - top & bottom, right & left

---

# 3. C****ss variable****

## var()

```css
var(custom-name)        /* lâý value của 1 custom-name */
var(custom-name, value) /* define variable + assign value cho variable + lấy ra chính value đó */
```

## live

- Nó không phải preprocessor giống như scss | sass
- Sử dụng như 1 công thức có thể thay đổi đầu vào

```html
<button class="btn">Hello</button>
<button class="btn red">Hello</button>
<button class="btn yellow">Hello</button>
<button class="btn green">Hello</button>
<button class="btn orange">Hello</button>
<button class="btn teal">Hello</button>
```

```css
.btn {
    padding: 2rem 4rem;
    border: 2px solid var(--color, black); //define varialbe + assign value
    background: transparent;
    font-size: 0.6em;
    border-radius: 2px;
}
.btn:hover {
    cursor: pointer;
    background: var(--color, black);//define varialbe + assign value
    color: white;
}

/* variations */

.btn.red {
    --color: red //assign giá trị khác cho varible
}
.btn.yellow {
    --color: yellow
}
.btn.green {
    --color: green
}
.btn.orange {
    --color: orange
}
.btn.teal {
    --color: teal
}
```

- chỉ có thể sử dụng variable trong scope mà nó được khai báo
- `:root` : khai báo global mà những file khác có thể sử dụng

---

# 4. R****elative units****

## Questions

[When coding, what types of units of measure do you typically use in css.](https://www.notion.so/When-coding-what-types-of-units-of-measure-do-you-typically-use-in-css-7171eaffdd874c2988c51ba8dd4b393d)

## em

- 1em = 1 x font-size of current element

## rem

- 1rem = 1 x root font-size

## @media

```html
all	    Default.    Used for all media type devices
print	              Used for printers
screen      	      Used for computer screens, tablets, smart-phones etc.
speech	            Used for screenreaders that "reads" the page out loud
```

```css
@media (min-width: 800px) { // Applies only to screens 800
    :root {                 // px and wider, overriding
        font-size: 0.875em; // the original value
    }
} 

@media (min-width: 1200px) { // Applies only to screens
    :root {                  // 1,200 px and larger,
        font-size: 1em;      // over
    }
}
```

---

# 5. ****margin****

## Questions

[How to center horizontally with CSS?](https://www.notion.so/How-to-center-horizontally-with-CSS-da2854e6cf89425888c5d20d0ff944be)

## ****Negative margin****

### **left**

div sẽ `CHIẾM` phần của left element (cùng z-index)

```css
----------------(!)-------------
!           |///(!)////////////|
!   left <= |///(!)////////////|
!           |///(!)////////////|
----------------(!)-------------
```

### **top**

div sẽ `CHIẾM` phần của top element (cùng z-index)

```css
..................
|      top       |
|       /\       |
|       ||       |
------------------
|////////////////|
..................
|////////////////|
|////////////////|
|////////////////|
------------------
```

### **right**

div sẽ `BỊ CHIẾM` bởi right element (cùng z-index)

```css
-------------------------------------
|/////////(!)/////////|           (!)
|/////////(!)right <= |           (!)
|/////////(!)/////////|           (!)
-------------------------------------
```

### **bottom**

div sẽ `BỊ CHIẾM` bởi bottom element (cùng z-index)

```css
..................
|                |
|                |
|                |
------------------
|////////////////|
..................
|////// || //////|
|////// \/ //////|
|//// bottom ////|
------------------
```

## **Margin collapse**

- Nếu 2 elements ngang hàng => margin giữa 2 element chọn cái lớn hơn (không phải tổng 2 cái)
- Chỉ xảy ra với chiều dọc (vertical), không xảy ra với chiều ngang horizontal

---

# 6. ****float****

## Questions

[Describe floats and how they work?](https://www.notion.so/Describe-floats-and-how-they-work-bed3798fbf534df2a71eb41adce023b8)

## Purpose of float

- Normal flow of the page : sắp xếp element tuân theo thứ tự trong code
- Floated element vẫn trong flow of the page nhưng không phải là normal flow
- Các elements trong normal flow ignore những floated elements và flow tiếp

## Float Collapsing

- Khi các children trong div đề là floated => normal flow rỗng => height = 0

---

# 7. ****display****

## Questions

[What is different between Block and Inline?](https://www.notion.so/What-is-different-between-Block-and-Inline-3c3ab4058722482f9b536bea810834d9)

[If use visible:hidden to hide, is that HTML node still existed?](https://www.notion.so/If-use-visible-hidden-to-hide-is-that-HTML-node-still-existed-6dab8fba398148c799fcd1f44ffb85e1)

## **inline**

- không chiếm dòng
- không custom kích thước (kích thước theo content) luôn có margin có sẵn

## **block**

- chiếm cả 1 dòng
- thay đổi margin để chiếm dòng đó
- custom kích thước

## **inline-block**

- hiển thị chiếm phần kích thước của nó

---

# 8. Flexbox

## Questions

[Do you know the concept of Flexbox? What are some of the basic features?](https://www.notion.so/Do-you-know-the-concept-of-Flexbox-What-are-some-of-the-basic-features-f364cf983b7d448cb37fdb356ef75d3d)

---

# 9. Position

## Questions

[What CSS property should be used to freeze a div?](https://www.notion.so/What-CSS-property-should-be-used-to-freeze-a-div-2b3d223926784352bba4f7bd37890bf7)

[How the position:inherit in CSS work?](https://www.notion.so/How-the-position-inherit-in-CSS-work-f10275f36d0f4c6796c7e7f6c290f431)

[What's the difference between a relative, fixed, absolute and statically positioned element?](https://www.notion.so/What-s-the-difference-between-a-relative-fixed-absolute-and-statically-positioned-element-4318eaf1bb3d4ff48349b509934d8567)

[Do you know what the position property has?](https://www.notion.so/Do-you-know-what-the-position-property-has-4fca5b502b174a678c4a5ff3ac5cef36)

[Do you know what sticky values are used for?](https://www.notion.so/Do-you-know-what-sticky-values-are-used-for-fb87c5b315874977bd3ea770d90016d7)

[What kind of position does z-index apply to?](https://www.notion.so/What-kind-of-position-does-z-index-apply-to-7308843b485645abb7cec3d9c4264734)

---

# 10. Grid

## Questions

[How to organize page layout SPA (how to use grid system)](https://www.notion.so/How-to-organize-page-layout-SPA-how-to-use-grid-system-d88607a806e7450095efb81532e6c656)

[Have you played around with the new CSS Flexbox or Grid specs?](https://www.notion.so/Have-you-played-around-with-the-new-CSS-Flexbox-or-Grid-specs-4d1ffb9335fa4cc58eb46eb8ee25c2af)

---