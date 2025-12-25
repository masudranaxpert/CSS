# Flexbox সম্পূর্ণ টিউটোরিয়াল 🚀

## 📌 Flexbox কী?

Flexbox হলো CSS-এর একটি Layout System যা দিয়ে তুমি সহজে responsive এবং flexible layout তৈরি করতে পারো। এটা দিয়ে তুমি elements গুলোকে row বা column-এ সাজাতে পারো এবং তাদের alignment, spacing, এবং size control করতে পারো।

**মূল ধারণা:**
- একটা **Flex Container** (parent)
- তার ভিতরে **Flex Items** (children)

---

## 🎯 Part 1: Native CSS Flexbox

### 1.1 Flex Container তৈরি করা

```css
.container {
  display: flex; /* এটাই flex container বানায় */
}
```

**কী হয়:**
- `display: flex;` দিলে একটা element flex container হয়ে যায়
- তার সব direct children automatically flex items হয়ে যায়

### 1.2 Main Axis এবং Cross Axis

Flexbox-এ দুইটা axis আছে:
- **Main Axis** (প্রধান অক্ষ): যেদিকে items সাজানো থাকে (default: horizontal/row)
- **Cross Axis** (ক্রস অক্ষ): main axis-এর perpendicular (default: vertical)

```
Main Axis (→)
┌─────────────────────────┐
│  [Item 1] [Item 2] [Item 3]  │ ↓ Cross Axis
└─────────────────────────┘
```

---

### 1.3 Flex Direction (দিক নির্ধারণ)

```css
.container {
  display: flex;
  flex-direction: row; /* default - বাম থেকে ডান */
}
```

**Options:**
- `row`: বাম থেকে ডান (default)
- `row-reverse`: ডান থেকে বাম
- `column`: উপর থেকে নিচে
- `column-reverse`: নিচে থেকে উপর

**উদাহরণ:**
```css
/* Horizontal Layout */
.container {
  display: flex;
  flex-direction: row;
}

/* Vertical Layout */
.container {
  display: flex;
  flex-direction: column;
}
```

---

### 1.4 Justify Content (Main Axis-এ Alignment)

Main axis বরাবর items কীভাবে সাজবে:

```css
.container {
  display: flex;
  justify-content: flex-start; /* default - শুরুতে */
}
```

**Options:**
- `flex-start`: শুরুতে সাজানো
- `flex-end`: শেষে সাজানো
- `center`: মাঝখানে সাজানো ⭐
- `space-between`: দুই পাশে items, মাঝে equal space
- `space-around`: প্রতি item-এর চারপাশে equal space
- `space-evenly`: সব জায়গায় equal space

**Visual Example:**
```
flex-start:    [1][2][3]_______
flex-end:      _______[1][2][3]
center:        ___[1][2][3]___
space-between: [1]___[2]___[3]
space-around:  _[1]__[2]__[3]_
space-evenly:  __[1]__[2]__[3]__
```

**তোমার প্রশ্নের উত্তর: `justify-center` মানে কী?**
`justify-center` (Native CSS-এ `justify-content: center;`) মানে হলো flex items গুলো main axis-এর মাঝখানে সাজানো হবে। যদি `flex-direction: row` থাকে তাহলে horizontally center হবে।

---

### 1.5 Align Items (Cross Axis-এ Alignment)

Cross axis বরাবর items কীভাবে align হবে:

```css
.container {
  display: flex;
  align-items: stretch; /* default - পুরো height নেয় */
}
```

**Options:**
- `stretch`: পুরো cross axis জুড়ে stretch হয়
- `flex-start`: cross axis-এর শুরুতে
- `flex-end`: cross axis-এর শেষে
- `center`: cross axis-এর মাঝখানে ⭐
- `baseline`: text baseline অনুযায়ী align


**উদাহরণ:**
```css
.container {
  display: flex;
  height: 200px;
  align-items: center; /* vertically center */
}
```

---

### 1.6 Flex Wrap (Wrapping)

যদি container-এ সব items fit না হয়, wrap করবে কিনা:

```css
.container {
  display: flex;
  flex-wrap: nowrap; /* default - wrap হবে না */
}
```

**Options:**
- `nowrap`: wrap হবে না (overflow হবে)
- `wrap`: wrap হবে, নতুন line-এ যাবে
- `wrap-reverse`: wrap হবে, কিন্তু reverse direction-এ

**Visual Example:**
```
nowrap:       [1][2][3][4][5]
wrap:         [1][2][3]
              [4][5]
wrap-reverse: [4][5]
              [1][2][3]
```

---

### 1.7 Gap (Items-এর মধ্যে Space)

Items-এর মধ্যে spacing দেওয়ার জন্য:

```css
.container {
  display: flex;
  gap: 16px; /* সব items-এর মধ্যে 16px gap */
}
```

**Options:**
- `gap: 20px;`: row এবং column উভয়ে 20px gap
- `row-gap: 10px;`: শুধু rows-এর মধ্যে gap
- `column-gap: 20px;`: শুধু columns-এর মধ্যে gap

**Visual Example:**
```
No Gap:  [1][2][3]
Gap:     [1] .. [2] .. [3]
            gap    gap
```

---

### 1.8 Flex Items-এর Properties

Individual items control করার জন্য:

#### 1.8.1 Flex Grow (বাড়ানো)

```css
.item {
  flex-grow: 1; /* available space proportionally নেবে */
}
```
- `flex-grow: 0;`: বাড়বে না (default)
- `flex-grow: 1;`: available space সমান ভাগে নেবে
- `flex-grow: 2;`: অন্যদের চেয়ে double space নেবে

**Visual Example:**
```
flex-grow: 0    [1][2]......
flex-grow: 1    [1......][2......]
```

#### 1.8.2 Flex Shrink (ছোট হওয়া)

```css
.item {
  flex-shrink: 1; /* জায়গা কম হলে shrink হবে */
}
```
- `flex-shrink: 0;`: shrink হবে না
- `flex-shrink: 1;`: shrink হতে পারবে (default)

**Visual Example:**
```
Container: [......]
No shrink: [11][22][33] (Overflows)
Shrink:    [1][2][3]    (Fits)
```

#### 1.8.3 Flex Basis (Initial Size)

```css
.item {
  flex-basis: 200px; /* initial width/height */
}
```

**Visual Example:**
```
flex-basis: 100px  [  100px  ]
flex-basis: 200px  [     200px     ]
```

#### 1.8.4 Flex Shorthand (একসাথে)

```css
.item {
  flex: 1; /* flex-grow: 1, flex-shrink: 1, flex-basis: 0 */
}

.item {
  flex: 0 0 200px; /* grow: 0, shrink: 0, basis: 200px */
}
```

**Common Patterns:**
- `flex: 1;`: equal space নেবে, flexible
- `flex: none;`: fixed size থাকবে
- `flex: auto;`: content অনুযায়ী size নেবে

**Visual Example:**
```
flex: 1 (Equal)  [  1  ][  2  ]
flex: none       [1][2]
```

#### 1.8.5 Align Self (Individual Alignment)

```css
.item {
  align-self: center; /* শুধু এই item-টা center হবে */
}
```

**Visual Example:**
```
Container (flex-start):
[1]      .       .
 .     [2]       .
 .      .       [3]
     (Self)
    (Center)
```

---

### 1.9 সম্পূর্ণ উদাহরণ (Native CSS)

```html
<!DOCTYPE html>
<html lang="bn">
<head>
  <style>
    .container {
      display: flex;
      flex-direction: row;
      justify-content: center;
      align-items: center;
      gap: 20px;
      height: 300px;
      background: #f0f0f0;
      padding: 20px;
    }

    .item {
      flex: 1;
      background: #3b82f6;
      color: white;
      padding: 20px;
      text-align: center;
      border-radius: 8px;
    }

    .item:nth-child(2) {
      flex: 2; /* এই item double space নেবে */
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="item">Item 1</div>
    <div class="item">Item 2 (Bigger)</div>
    <div class="item">Item 3</div>
  </div>
</body>
</html>
```

---

## 🎨 Part 2: Tailwind CSS Flexbox

Tailwind-এ flexbox ব্যবহার করা অনেক সহজ! প্রতিটা CSS property-র জন্য utility class আছে।

### 2.1 Flex Container তৈরি

```html
<div class="flex">
  <!-- Flex items here -->
</div>
```

এটাই! শুধু `flex` class দিলেই `display: flex;` হয়ে যায়।

---

### 2.2 Flex Direction

| CSS | Tailwind |
|-----|----------|
| `flex-direction: row;` | `flex-row` |
| `flex-direction: row-reverse;` | `flex-row-reverse` |
| `flex-direction: column;` | `flex-col` |
| `flex-direction: column-reverse;` | `flex-col-reverse` |

**উদাহরণ:**
```html
<!-- Horizontal -->
<div class="flex flex-row">
  <div>Item 1</div>
  <div>Item 2</div>
</div>

<!-- Vertical -->
<div class="flex flex-col">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

---

### 2.3 Justify Content

| CSS | Tailwind |
|-----|----------|
| `justify-content: flex-start;` | `justify-start` |
| `justify-content: flex-end;` | `justify-end` |
| `justify-content: center;` | `justify-center` ⭐ |
| `justify-content: space-between;` | `justify-between` |
| `justify-content: space-around;` | `justify-around` |
| `justify-content: space-evenly;` | `justify-evenly` |

**উদাহরণ:**
```html
<!-- Center horizontally -->
<div class="flex justify-center">
  <div>Centered!</div>
</div>

<!-- Space between -->
<div class="flex justify-between">
  <div>Left</div>
  <div>Right</div>
</div>
```

---

### 2.4 Align Items

| CSS | Tailwind |
|-----|----------|
| `align-items: stretch;` | `items-stretch` |
| `align-items: flex-start;` | `items-start` |
| `align-items: flex-end;` | `items-end` |
| `align-items: center;` | `items-center` ⭐ |
| `align-items: baseline;` | `items-baseline` |

**উদাহরণ:**
```html
<!-- Center vertically -->
<div class="flex items-center h-64">
  <div>Vertically Centered!</div>
</div>

<!-- Center both horizontally and vertically -->
<div class="flex justify-center items-center h-screen">
  <div>Perfect Center!</div>
</div>
```

---

### 2.5 Flex Wrap

| CSS | Tailwind |
|-----|----------|
| `flex-wrap: nowrap;` | `flex-nowrap` |
| `flex-wrap: wrap;` | `flex-wrap` |
| `flex-wrap: wrap-reverse;` | `flex-wrap-reverse` |

**উদাহরণ:**
```html
<div class="flex flex-wrap gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
  <!-- Wrap হবে যদি space না থাকে -->
</div>
```

---

### 2.6 Gap

| CSS | Tailwind |
|-----|----------|
| `gap: 4px;` | `gap-1` |
| `gap: 8px;` | `gap-2` |
| `gap: 16px;` | `gap-4` |
| `gap: 24px;` | `gap-6` |
| `gap: 32px;` | `gap-8` |
| `row-gap: 16px;` | `gap-y-4` |
| `column-gap: 16px;` | `gap-x-4` |

**Tailwind Gap Scale:**
- `gap-0`: 0px
- `gap-1`: 4px
- `gap-2`: 8px
- `gap-3`: 12px
- `gap-4`: 16px
- `gap-5`: 20px
- `gap-6`: 24px
- `gap-8`: 32px
- `gap-10`: 40px
- `gap-12`: 48px

**উদাহরণ:**
```html
<div class="flex gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

---

### 2.7 Flex Items

#### 2.7.1 Flex Grow

| CSS | Tailwind |
|-----|----------|
| `flex-grow: 0;` | `grow-0` |
| `flex-grow: 1;` | `grow` |

**উদাহরণ:**
```html
<div class="flex">
  <div class="grow">This will take available space</div>
  <div>Fixed size</div>
</div>
```

#### 2.7.2 Flex Shrink

| CSS | Tailwind |
|-----|----------|
| `flex-shrink: 0;` | `shrink-0` |
| `flex-shrink: 1;` | `shrink` |

#### 2.7.3 Flex Basis

```html
<div class="flex">
  <div class="basis-64">256px initial width</div>
  <div class="basis-1/3">33.33% width</div>
  <div class="basis-1/2">50% width</div>
</div>
```

#### 2.7.4 Flex Shorthand

| CSS | Tailwind |
|-----|----------|
| `flex: 1 1 0%;` | `flex-1` ⭐ |
| `flex: 1 1 auto;` | `flex-auto` |
| `flex: 0 1 auto;` | `flex-initial` |
| `flex: none;` | `flex-none` |

**Most Common:**
```html
<!-- Equal width columns -->
<div class="flex gap-4">
  <div class="flex-1">Column 1</div>
  <div class="flex-1">Column 2</div>
  <div class="flex-1">Column 3</div>
</div>
```

---

### 2.8 Align Self

| CSS | Tailwind |
|-----|----------|
| `align-self: auto;` | `self-auto` |
| `align-self: flex-start;` | `self-start` |
| `align-self: flex-end;` | `self-end` |
| `align-self: center;` | `self-center` |
| `align-self: stretch;` | `self-stretch` |

---

### 2.9 সম্পূর্ণ উদাহরণ (Tailwind)

```html
<!DOCTYPE html>
<html lang="bn">
<head>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
  <!-- Navigation Bar -->
  <nav class="flex justify-between items-center bg-blue-600 text-white p-4">
    <div class="text-xl font-bold">Logo</div>
    <div class="flex gap-6">
      <a href="#">Home</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </div>
  </nav>

  <!-- Hero Section -->
  <section class="flex justify-center items-center h-screen bg-gray-100">
    <div class="text-center">
      <h1 class="text-4xl font-bold mb-4">Welcome!</h1>
      <p class="text-gray-600">This is centered perfectly</p>
    </div>
  </section>

  <!-- Card Grid -->
  <div class="flex flex-wrap gap-6 p-8">
    <div class="flex-1 min-w-[250px] bg-white p-6 rounded-lg shadow">
      <h3 class="text-xl font-bold mb-2">Card 1</h3>
      <p class="text-gray-600">Content here</p>
    </div>
    <div class="flex-1 min-w-[250px] bg-white p-6 rounded-lg shadow">
      <h3 class="text-xl font-bold mb-2">Card 2</h3>
      <p class="text-gray-600">Content here</p>
    </div>
    <div class="flex-1 min-w-[250px] bg-white p-6 rounded-lg shadow">
      <h3 class="text-xl font-bold mb-2">Card 3</h3>
      <p class="text-gray-600">Content here</p>
    </div>
  </div>
</body>
</html>
```

---

## 🔥 Common Patterns

### Pattern 1: Perfect Center
```html
<div class="flex justify-center items-center h-screen">
  <div>Centered Content</div>
</div>
```

### Pattern 2: Navbar
```html
<nav class="flex justify-between items-center p-4 bg-gray-800 text-white">
  <div>Logo</div>
  <div class="flex gap-4">
    <a href="#">Link 1</a>
    <a href="#">Link 2</a>
  </div>
</nav>
```

### Pattern 3: Equal Columns
```html
<div class="flex gap-4">
  <div class="flex-1 bg-blue-100 p-4">Column 1</div>
  <div class="flex-1 bg-green-100 p-4">Column 2</div>
  <div class="flex-1 bg-red-100 p-4">Column 3</div>
</div>
```

### Pattern 4: Sidebar Layout
```html
<div class="flex h-screen">
  <aside class="w-64 bg-gray-800 text-white p-4">Sidebar</aside>
  <main class="flex-1 p-8">Main Content</main>
</div>
```

### Pattern 5: Card with Footer at Bottom
```html
<div class="flex flex-col h-full">
  <div class="flex-1">
    <h2>Card Title</h2>
    <p>Content here...</p>
  </div>
  <div class="border-t pt-4">Footer always at bottom</div>
</div>
```

---

## 📚 Quick Reference

### Container Properties
```
display: flex             → flex
flex-direction: row       → flex-row
flex-direction: column    → flex-col
justify-content: center   → justify-center
align-items: center       → items-center
gap: 16px                → gap-4
flex-wrap: wrap          → flex-wrap
```

### Item Properties
```
flex: 1                  → flex-1
flex-grow: 1             → grow
flex-shrink: 0           → shrink-0
flex-basis: 200px        → basis-[200px]
align-self: center       → self-center
```

---

## 💡 Tips and Tricks

1. **Perfect Center (Horizontal + Vertical):**
   ```html
   <div class="flex justify-center items-center h-screen">
     <div>Centered!</div>
   </div>
   ```

2. **Responsive Direction:**
   ```html
   <div class="flex flex-col md:flex-row">
     <!-- Mobile: vertical, Desktop: horizontal -->
   </div>
   ```

3. **Space Between with Gap:**
   ```html
   <div class="flex justify-between items-center gap-4">
     <!-- Items spread out with minimum gap -->
   </div>
   ```

4. **One Item Takes Remaining Space:**
   ```html
   <div class="flex gap-4">
     <div>Fixed</div>
     <div class="flex-1">Takes remaining space</div>
     <div>Fixed</div>
   </div>
   ```

5. **Responsive Gap:**
   ```html
   <div class="flex gap-2 md:gap-4 lg:gap-8">
     <!-- Gap increases on larger screens -->
   </div>
   ```

---
