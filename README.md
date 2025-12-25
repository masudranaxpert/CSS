# CSS Flexbox টিউটোরিয়াল

এই গাইডটি CSS Flexbox সম্পর্কে সম্পূর্ণ তথ্য প্রদান করে। Flexbox আধুনিক ওয়েব ডিজাইনের জন্য একটি শক্তিশালী লেআউট সিস্টেম।

## Flexbox কি?

Flexbox হল CSS এর একটি নমনীয় বক্স মডেল যা আপনাকে এক-মাত্রিক লেআউট তৈরি করতে সাহায্য করে। এটি আইটেমগুলিকে সারিবদ্ধ করা, বিতরণ করা এবং নমনীয় আকারের সাথে পরিচালনা করা সহজ করে তোলে।

## মূল ধারণা

### 1. Flex Container এবং Flex Items

```css
/* Flex Container */
.container {
  display: flex;
}

/* Flex Items - Container এর সরাসরি সন্তান উপাদান */
.container > .item {
  /* এখানে Flexbox প্রপার্টি প্রয়োগ করা হয় */
}
```

**ভিজ্যুয়াল উদাহরণ:**
```
┌─────────────────────────────────┐
│  Flex Container                 │
│  ┌───────┐ ┌───────┐ ┌───────┐ │
│  │ Item1 │ │ Item2 │ │ Item3 │ │
│  └───────┘ └───────┘ └───────┘ │
└─────────────────────────────────┘
```

## Flex Container প্রপার্টিসমূহ

### 1. display: flex

```css
.container {
  display: flex; /* আইটেমগুলি পাশাপাশি সাজানো হয় */
}
```

### 2. flex-direction

আইটেমগুলির দিকনির্দেশনা নির্ধারণ করে।

```css
.container {
  flex-direction: row;           /* বাম থেকে ডান (ডিফল্ট) */
  /* flex-direction: row-reverse; */ /* ডান থেকে বাম */
  /* flex-direction: column;       */ /* উপর থেকে নিচ */
  /* flex-direction: column-reverse;*/ /* নিচ থেকে উপর */
}
```

**ভিজ্যুয়াল উদাহরণ:**

```
row:
┌─────────────────────────┐
│ [1] [2] [3]            │
└─────────────────────────┘

row-reverse:
┌─────────────────────────┐
│            [3] [2] [1]  │
└─────────────────────────┘

column:
┌──────┐
│ [1]  │
│ [2]  │
│ [3]  │
└──────┘

column-reverse:
┌──────┐
│ [3]  │
│ [2]  │
│ [1]  │
└──────┘
```

### 3. justify-content

প্রধান অক্ষে (Main Axis) আইটেমগুলির সারিবদ্ধতা নিয়ন্ত্রণ করে।

```css
.container {
  justify-content: flex-start;    /* শুরুতে সাজানো (ডিফল্ট) */
  /* justify-content: flex-end;      */ /* শেষে সাজানো */
  /* justify-content: center;         */ /* মাঝে সাজানো */
  /* justify-content: space-between;  */ /* সমান ব্যবধান মধ্যে */
  /* justify-content: space-around;   */ /* সমান ব্যবধান চারপাশে */
  /* justify-content: space-evenly;   */ /* সম্পূর্ণ সমান ব্যবধান */
}
```

**ভিজ্যুয়াল উদাহরণ:**

```
flex-start:
┌──────────────────────────────┐
│ [1] [2] [3]                  │
└──────────────────────────────┘

flex-end:
┌──────────────────────────────┐
│                    [1] [2] [3]│
└──────────────────────────────┘

center:
┌──────────────────────────────┐
│        [1] [2] [3]           │
└──────────────────────────────┘

space-between:
┌──────────────────────────────┐
│ [1]        [2]        [3]    │
└──────────────────────────────┘

space-around:
┌──────────────────────────────┐
│  [1]       [2]       [3]     │
└──────────────────────────────┘

space-evenly:
┌──────────────────────────────┐
│  [1]      [2]      [3]       │
└──────────────────────────────┘
```

### 4. align-items

ক্রস অক্ষে (Cross Axis) আইটেমগুলির সারিবদ্ধতা নিয়ন্ত্রণ করে।

```css
.container {
  align-items: stretch;      /* প্রসারিত করুন (ডিফল্ট) */
  /* align-items: flex-start;  */ /* উপরে সাজানো */
  /* align-items: flex-end;    */ /* নিচে সাজানো */
  /* align-items: center;      */ /* মাঝে সাজানো */
  /* align-items: baseline;    */ /* বেসলাইন অনুযায়ী */
}
```

**ভিজ্যুয়াল উদাহরণ (Column প্রসঙ্গে):**

```
stretch:
┌──────────────────────┐
│ [1] [2] [3]         │
│ │   │   │           │
│ │   │   │  (উচ্চতা) │
│ │   │   │           │
└──────────────────────┘

flex-start:
┌──────────────────────┐
│ [1] [2] [3]         │
│                     │
│                     │
│                     │
└──────────────────────┘

center:
┌──────────────────────┐
│                     │
│ [1] [2] [3]         │
│                     │
└──────────────────────┘
```

### 5. flex-wrap

আইটেমগুলি পরবর্তী লাইনে যেতে পারবে কিনা তা নির্ধারণ করে।

```css
.container {
  flex-wrap: nowrap;    /* এক লাইনে থাকুন (ডিফল্ট) */
  /* flex-wrap: wrap;      */ /* প্রয়োজনে পরবর্তী লাইনে যান */
  /* flex-wrap: wrap-reverse; */ /* বিপরীত দিকে মোড়ান */
}
```

**ভিজ্যুয়াল উদাহরণ:**

```
nowrap (সব এক লাইনে):
┌────────────────────────┐
│ [1] [2] [3] [4] [5]    │
└────────────────────────┘

wrap (প্রয়োজন অনুযায়ী):
┌────────────────────────┐
│ [1] [2] [3]            │
│ [4] [5]                │
└────────────────────────┘
```

### 6. gap

আইটেমগুলির মধ্যে ব্যবধান সেট করে।

```css
.container {
  gap: 20px;              /* সব দিকে ২০px ব্যবধান */
  /* gap: 20px 30px;        */ /* row-gap: 20px, column-gap: 30px */
  /* row-gap: 20px;         */ /* শুধুমাত্র সারি ব্যবধান */
  /* column-gap: 30px;      */ /* শুধুমাত্র কলাম ব্যবধান */
}
```

**ভিজ্যুয়াল উদাহরণ:**

```
gap: 20px:
┌─────────────────────────────────┐
│ [1]  ░░  [2]  ░░  [3]          │
│  ░░░░░░░░░░░░░░░░░░░░░░░░░░    │
│ [4]  ░░  [5]  ░░  [6]          │
└─────────────────────────────────┘
(░░ = গ্যাপ)
```

## Flex Items প্রপার্টিসমূহ

### 1. flex-grow

আইটেমটি উপলব্ধ স্থান গ্রহণ করার ক্ষমতা নির্ধারণ করে।

```css
.item {
  flex-grow: 1;  /* অন্যান্য আইটেমের তুলনায় ২ গুণ বৃদ্ধি পান */
}
```

**ভিজ্যুয়াল উদাহরণ:**

```
flex-grow: 1, 0, 1:
┌───────────────────────────────────┐
│ [1]        [2]        [3]         │
│ ░░░░░░     (fixed)   ░░░░░░       │
└───────────────────────────────────┘
```

### 2. flex-shrink

আইটেমটি সংকুচিত হওয়ার ক্ষমতা নির্ধারণ করে।

```css
.item {
  flex-shrink: 1;  /* আইটেম সংকুচিত হতে পারে */
  /* flex-shrink: 0;  */ /* আইটেম সংকুচিত হবে না */
}
```

### 3. flex-basis

আইটেমের প্রাথমিক আকার নির্ধারণ করে।

```css
.item {
  flex-basis: 200px;  /* প্রাথমিক প্রস্থ ২০০px */
  /* flex-basis: auto; */ /* স্বয়ংক্রিয় (ডিফল্ট) */
}
```

### 4. flex সংক্ষিপ্ত রূপ

সব তিনটি প্রপার্টি একসাথে সেট করে।

```css
.item {
  flex: 1 1 200px;  /* flex-grow flex-shrink flex-basis */
}
```

**সাধারণ মান:**

```css
flex: 0 1 auto;     /* ডিফল্ট */
flex: 1;            /* 1 1 0 এর সমান */
flex: auto;         /* 1 1 auto এর সমান */
flex: none;         /* 0 0 auto এর সমান */
```

### 5. align-self

নির্দিষ্ট আইটেমের জন্য ক্রস অক্ষ সারিবদ্ধতা।

```css
.item {
  align-self: auto;       /* Container এর align-items অনুসরণ করুন */
  /* align-self: flex-start;  */
  /* align-self: flex-end;    */
  /* align-self: center;      */
  /* align-self: stretch;     */
}
```

### 6. order

আইটেমের প্রদর্শনের ক্রম পরিবর্তন করে (DOM ক্রমে নয়)।

```css
.item {
  order: 1;  /* ডিফল্ট ০। কম নম্বর আগে দেখা যায় */
}

.item:nth-child(1) { order: 3; }  /* তৃতীয় অবস্থানে */
.item:nth-child(2) { order: 1; }  /* প্রথম অবস্থানে */
.item:nth-child(3) { order: 2; }  /* দ্বিতীয় অবস্থানে */
```

## বাস্তব জীবনের উদাহরণ

### উদাহরণ ১: নেভিগেশন বার

```html
<nav class="navbar">
  <div class="logo">লোগো</div>
  <ul class="nav-links">
    <li><a href="#">হোম</a></li>
    <li><a href="#">পণ্য</a></li>
    <li><a href="#">যোগাযোগ</a></li>
  </ul>
</nav>
```

```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  background-color: #333;
}

.nav-links {
  display: flex;
  gap: 2rem;
  list-style: none;
}

.nav-links a {
  color: white;
  text-decoration: none;
}
```

**লেআউট:**
```
┌──────────────────────────────────────┐
│ লোগো        হোম পণ্য যোগাযোগ      │
└──────────────────────────────────────┘
```

### উদাহরণ ২: কার্ড গ্রিড

```html
<div class="cards-container">
  <div class="card">
    <h3>কার্ড ১</h3>
    <p>কন্টেন্ট</p>
  </div>
  <div class="card">
    <h3>কার্ড ২</h3>
    <p>কন্টেন্ট</p>
  </div>
  <div class="card">
    <h3>কার্ড ৩</h3>
    <p>কন্টেন্ট</p>
  </div>
</div>
```

```css
.cards-container {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  justify-content: center;
}

.card {
  flex: 0 1 300px;  /* সর্বনিম্ন ৩০০px, বৃদ্ধি হবে না */
  border: 1px solid #ddd;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
```

**লেআউট:**
```
┌─────────────────────────────────────┐
│  ┌────────┐  ┌────────┐ ┌────────┐ │
│  │ কার্ড ১│ │ কার্ড ২ │ │ কার্ড ৩│ │
│  │        │  │        │ │        │ │
│  └────────┘  └────────┘ └────────┘ │
└─────────────────────────────────────┘
```

### উদাহরণ ৩: সেন্টারড কন্টেন্ট

```css
.centered-container {
  display: flex;
  justify-content: center;  /* অনুভূমিক কেন্দ্র */
  align-items: center;      /* উল্লম্ব কেন্দ্র */
  height: 100vh;            /* সম্পূর্ণ ভিউপোর্ট উচ্চতা */
}

.centered-content {
  text-align: center;
}
```

**লেআউট:**
```
┌────────────────────────┐
│                        │
│                        │
│    আপনার কন্টেন্ট   │
│                        │
│                        │
└────────────────────────┘
```

## Flex এর সুবিধা

| সুবিধা | বর্ণনা |
|--------|--------|
| **সহজ সারিবদ্ধতা** | কোনো হ্যাক ছাড়াই আইটেম সারিবদ্ধ করুন |
| **প্রতিক্রিয়াশীল** | বিভিন্ন স্ক্রীন সাইজে স্বয়ংক্রিয় সমন্বয় |
| **নমনীয়তা** | আইটেম আকার এবং ব্যবধান গতিশীলভাবে পরিচালনা করুন |
| **সহজ আদেশ পরিবর্তন** | CSS দিয়ে উপাদান ক্রম পুনর্বিন্যাস করুন |
| **ব্রাউজার সমর্থন** | সমস্ত আধুনিক ব্রাউজারে সমর্থিত |

## সাধারণ সমস্যা এবং সমাধান

### সমস্যা ১: আইটেম উচ্চতা প্রসারিত হচ্ছে না

**কারণ:** `align-items: stretch` সক্রিয় নয়

**সমাধান:**
```css
.container {
  display: flex;
  align-items: stretch;  /* বা এটি ডিফল্ট */
  height: 200px;        /* কন্টেইনার উচ্চতা প্রয়োজন */
}
```

### সমস্যা ২: আইটেম সংকুচিত হচ্ছে

**কারণ:** `flex-shrink` ডিফল্টভাবে সক্রিয়

**সমাধান:**
```css
.item {
  flex-shrink: 0;  /* সংকুচিত হবে না */
}
```

### সমস্যা ৩: Gap কাজ করছে না

**কারণ:** পুরানো ব্রাউজার

**সমাধান (Fallback):**
```css
.container {
  gap: 1rem;
  margin: -0.5rem;  /* পুরানো ব্রাউজারের জন্য */
}

.item {
  margin: 0.5rem;
}
```

## ব্রাউজার সমর্থন

| ফিচার | Chrome | Firefox | Safari | Edge |
|--------|--------|---------|--------|------|
| display: flex | ✓ | ✓ | ✓ | ✓ |
| flex-direction | ✓ | ✓ | ✓ | ✓ |
| justify-content | ✓ | ✓ | ✓ | ✓ |
| align-items | ✓ | ✓ | ✓ | ✓ |
| flex-wrap | ✓ | ✓ | ✓ | ✓ |
| gap | ✓ | ✓ | ✓ | ✓ |

## সংক্ষিপ্ত রেফারেন্স গাইড

### Container প্রপার্টি
```css
display: flex;
flex-direction: row | column | row-reverse | column-reverse;
justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
align-items: stretch | flex-start | flex-end | center | baseline;
align-content: flex-start | flex-end | center | space-between | space-around | stretch;
flex-wrap: nowrap | wrap | wrap-reverse;
gap: <length> [<length>];
```

### Item প্রপার্টি
```css
flex: <grow> <shrink> <basis>;
flex-grow: <number>;
flex-shrink: <number>;
flex-basis: <length> | auto;
align-self: auto | flex-start | flex-end | center | baseline | stretch;
order: <integer>;
```

## উপসংহার

Flexbox আধুনিক ওয়েব ডিজাইনের একটি অপরিহার্য হাতিয়ার। এটি লেআউট তৈরি করা সহজ করে এবং প্রতিক্রিয়াশীল ডিজাইন সক্ষম করে। এই টিউটোরিয়ালের ধারণাগুলি অনুশীলন করুন এবং আপনি শীঘ্রই একজন Flexbox বিশেষজ্ঞ হয়ে উঠবেন!

---

**শেষ আপডেট:** ২০২৫-১২-২৫
