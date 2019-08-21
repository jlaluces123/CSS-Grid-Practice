# CSS-Grid-Practice
Since I solely use flexbox, I thought about giving Grid a shot!

---


## Simplifying

Before:
```css

/* style.css */

main {
  height: 100vh;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr;
}

.box1 {
  grid-column: ##;
  grid-row: ##
}

.box2 {
  grid-column: ##;
  grid-row: ##
}

.box3 {
  grid-column: ##;
  grid-row: ##
}

```

- Instead, we can simplify it with `grid-template areas`:
  1. first we name the box-classes with `grid-area`
  2. then we can lay them out as we see fit with `template-areas`
  3. by adding a `.`, it will leave that grid space empty
    - ex) "box1 box2" \n "box3 ."

After:
```css
/* style.css */

main {
  /* { ... } */
  grid-template-areas:
    "box1 box2"
    "box3 box3";
}

.box1 {
  grid-area: box1;
}

.box2 {
  grid-area: box2;
}

.box3 {
  grid-area: box3;
}

```

---

## Simplifying Pt.2

Before:
```css

.img__gallery {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
```

After:
```css

.img__gallery {
  display: grid;
  grid-template-columns: repeat(3, 200px);
}

```

- For responsive we can use `autofill`
  - This will let CSS grid define how much space it needs to use
  - It basically generate another column if given the correct spacing
  - GENERALLY: we use `auto-fit` as to not auto-generate new columns

```css

.img__gallery {
  display: grid;
  grid-template-columns: repeat(autofill, 300px);
}

```

### minmax()

- This allows us the ability to define the min-value a picture should have
  - Then as soon as the picture has more space we can define the max-value we want for it

```css

.img__gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}

```

- To get spacing between grid-columns or grid-rows (pretty much like margin), we can use `grid-row-gap: # || grid-column-gap: #`

```css

.img__gallery {
  display: grid;
  grid-template-columns: repeat(autofill, 300px);
  grid-column-gap: 20px;
  grid-row-gap: 20px;
}

```