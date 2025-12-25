# Flexbox ফুল টিউটোরিয়াল (বাংলায়)

Flexbox (Flexible Box Layout) হলো CSS-এর একটা শক্তিশালী লেআউট সিস্টেম। এটা দিয়ে খুব সহজেই আইটেমগুলোকে একটা কন্টেইনারের ভিতর অ্যালাইন করা, স্পেস ডিস্ট্রিবিউট করা এবং রেসপনসিভ লেআউট বানানো যায়। Flexbox মূলত ১-ডাইমেনশনাল লেআউটের জন্য।

## Flexbox কীভাবে কাজ করে?

- **Flex Container**: প্যারেন্ট এলিমেন্ট (`display: flex;`)
- **Flex Items**: চাইল্ড এলিমেন্টগুলো

### Main Axis ও Cross Axis
- Main Axis: আইটেম সাজানোর দিক (ডিফল্ট horizontal)
- Cross Axis: তার লম্বালম্বি দিক (ডিফল্ট vertical)

## ১. Native CSS দিয়ে Flexbox

### Container প্রপার্টি

```css
.container {
  display: flex; /* বা inline-flex */

  flex-direction: row; /* row | row-reverse | column | column-reverse */
  flex-wrap: nowrap; /* nowrap | wrap | wrap-reverse */
  flex-flow: row wrap; /* shorthand */

  justify-content: flex-start; /* main axis: flex-start | flex-end | center | space-between | space-around | space-evenly */
  align-items: stretch; /* cross axis: stretch | flex-start | flex-end | center | baseline */
  align-content: stretch; /* multi-line এর জন্য */

  gap: 1rem; /* space between items */
}
```

### Item প্রপার্টি

```css
.item {
  flex-grow: 0; /* extra space পেলে আইটেম বড় হবে */
  flex-shrink: 1; /* স্পেস কমলে ছোট হবে */
  flex-basis: auto; /* initial size */
  flex: 0 1 auto; /* shorthand */

  align-self: auto; /* individual cross axis alignment */
  order: 0; /* sequence change */
}
```

### উদাহরণ

```css
.container-example {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 400px;
  background: #f0f0f0;
}
```

## ২. Tailwind CSS দিয়ে (v4 অনুযায়ী)

নিচে Tailwind ক্লাসের মাধ্যমে কনটেইনার ও আইটেম প্রপার্টিগুলোর সমতুল্য দেখানো হলো:

কনটেইনার (Container)

| কাজ | Tailwind ক্লাস | CSS সমতুল্য |
|---|---:|---|
| Flex চালু | `flex` / `inline-flex` | `display: flex;` / `display: inline-flex;` |
| দিক | `flex-row`, `flex-col`, `flex-row-reverse`, `flex-col-reverse` | `flex-direction` |
| Wrap | `flex-wrap`, `flex-nowrap`, `flex-wrap-reverse` | `flex-wrap` |
| Main axis alignment | `justify-start`, `justify-end`, `justify-center`, `justify-between`, `justify-around`, `justify-evenly` | `justify-content` |
| Cross axis (single line) | `items-start`, `items-end`, `items-center`, `items-stretch`, `items-baseline` | `align-items` |
| Cross axis (multi-line) | `content-start`, `content-center`, `content-end`, `content-between`, `content-around`, `content-evenly` | `align-content` |
| Gap | `gap-1`, `gap-2`, `gap-4`, `gap-x-8`, `gap-y-4` | `gap` |

আইটেম (Item)

| কাজ | Tailwind ক্লাস | CSS সমতুল্য |
|---|---:|---|
| Grow / Shrink | `flex-1`, `flex-auto`, `flex-none`, `flex-initial` | `flex` shorthand / `flex-grow` / `flex-shrink` |
| Align self | `self-auto`, `self-start`, `self-end`, `self-center`, `self-stretch` | `align-self` |
| Order | `order-1`, `order-2`, `order-first`, `order-last` | `order` |

Tailwind উদাহরণ:

```html
<div class="flex flex-col md:flex-row justify-center items-center gap-8 min-h-screen bg-gray-100">
  <div class="flex-1 bg-blue-400 p-10">আইটেম ১</div>
  <div class="flex-none bg-green-400 p-10">আইটেম ২</div>
  <div class="flex-1 bg-red-400 p-10">আইটেম ৩</div>
</div>
```

প্র্যাকটিস লিঙ্ক

- Tailwind Play: https://play.tailwindcss.com/
- Flexbox Froggy: https://flexboxfroggy.com/

Happy Coding ভাই! 🚀
