# BEM Standard

Category: CSS
First Refrence: What%20is%20BEM%20cd8751665001480db5c3ae10e91d0487.md, What%20is%20Modifier%20in%20BEM%203a238192177a4142a603ccf8022d934a.md
Tags: Common, Concept

**Recall**

## Concept

- BEM stands for Block - Element - Modifier
- Block: Standalone entity that is meaningful on its own.
    - `header`
    - `container`
    - `menu`
    - `checkbox`
    - `input`
- Element: A part of a block that has no standalone meaning and is semantically tied to its block.
    - `menu item`
    - `list item`
    - `checkbox caption`
    - `header title`
- Modifier: A flag on a block or element. Use them to change appearance or behavior.
    - Use them to change appearance or behavior.
    - `disabled`
    - `highlighted`
    - `checked`
    - `fixed`
    - `size big`
    - `color yellow`

## Benifit

### **Structure**

- BEM methodology gives your CSS code a solid structure that remains simple and easy to understand.

### **Modularity**

- Block styles are never dependent on other elements on a page, so you will never experience problems from cascading.
    - Avoid overwrite one class many times.
- You also get the ability to transfer blocks from your finished projects to new ones.

### **Reusability**

- Composing independent blocks in different ways.
    - Like make a UI Kit, Css Library.
- Reusing them intelligently, reduces the amount of CSS code that you will have to maintain.
- With a set of style guidelines in place, you can build a library of blocks, making your CSS super effective.

---

# Vocabulary

- Modularity: Mô đun hóa
- Cascade: xếp tầng