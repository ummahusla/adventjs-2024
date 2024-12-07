# 📦 Is the gift inside the box?

### Description

We have already wrapped hundreds of presents 🎁… but an elf forgot to check if the present, represented by an asterisk *, is inside the box.

The box has a present (*) and counts as "inside the box" if:

* It is completely surrounded by # on the box's edges.
* The * is not on the box's edges.


Keep in mind that the * can be inside, outside, or may not even be there. We must return true if the * is inside the box and false otherwise.

Examples:
```js
inBox([
  "###",
  "#*#",
  "###"
]) // ➞ true

inBox([
  "####",
  "#* #",
  "#  #",
  "####"
]) // ➞ true

inBox([
  "#####",
  "#   #",
  "#  #*",
  "#####"
]) // ➞ false

inBox([
  "#####",
  "#   #",
  "#   #",
  "#   #",
  "#####"
]) // ➞ false
```

### Solution (5/5 stars)

```js
function inBox(box) {
  for (let i = 1; i < box.length - 1; i++) {
    if (box[i][0] !== '#' || box[i][box[i].length - 1] !== '#') return false;
    if (box[i].includes('*')) return true;
  }
  return false;
}
```
