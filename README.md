## 🗓️ Day 17: HTML Images & CSS Box Model

**Focus:** Frontend visuals and layout spacing.

### 🖼️ HTML Images
The `<img>` tag embeds images. The most critical attribute is `src` (Source).
```html
<!-- Example of a standard image insertion -->
<img src="hacker-setup.jpg" alt="My Hacking Station" width="500">
📦 CSS Box Model: Padding vs. Margin
The "Box Model" wraps every HTML element.

Content: The actual image or text.

Padding: Space between content and the border (Inside).

Border: The edge around the padding.

Margin: Space outside the border (Outside).

Visual Analogy:

Padding is like wearing a thick winter coat (adds bulk to you).

Margin is like social distancing (adds space between you and others).

css
.box {
  border: 2px solid red;
  padding: 20px; /* Space inside the red border */
  margin: 50px;  /* Space outside the red border */
}
