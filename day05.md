Santa Claus's elves 🧝🧝‍♂️ have found a bunch of mismatched magic boots in the workshop. Each boot is described by two values:

* type indicates if it's a left boot (I) or a right boot (R).
* size indicates the size of the boot.
Your task is to help the elves pair all the boots of the same size having a left and a right one. To do this, you should return a list of the available boots after pairing them.

Note: You can have more than one pair of boots of the same size!

```js
const shoes = [
  { type: 'I', size: 38 },
  { type: 'R', size: 38 },
  { type: 'R', size: 42 },
  { type: 'I', size: 41 },
  { type: 'I', size: 42 }
]

organizeShoes(shoes)
// [38, 42]

const shoes2 = [
  { type: 'I', size: 38 },
  { type: 'R', size: 38 },
  { type: 'I', size: 38 },
  { type: 'I', size: 38 },
  { type: 'R', size: 38 }
]
// [38, 38]

const shoes3 = [
  { type: 'I', size: 38 },
  { type: 'R', size: 36 },
  { type: 'R', size: 42 },
  { type: 'I', size: 41 },
  { type: 'I', size: 43 }
]

organizeShoes(shoes3)
// []
```

# Solution (1/5 stars)

```js
function organizeShoes(shoes) {
  let pairs = [];
  let map = {};

  for (let i = 0; i < shoes.length; i++) {
    const {type, size} = shoes[i];
    
    if (!map[size]) {
      map[size] = {
        "I": 0,
        "R": 0,
      };
    }
    
    map[size][type] = map[size][type] + 1;
  }
  
  Object.keys(map).map((key) => {
    if(map[key].I > 0 && map[key].R > 0) {
      if(Math.min(map[key].I, map[key].R)) {
        pairs.push(...Array(Math.min(map[key].I, map[key].R)).fill(Number(key)));
      }
    }
  });

  return pairs;
}
```
