# 🚂 The magic train

### Description

The elves are playing with a magical train 🚂 that carries gifts. This train moves on a board represented by an array of strings.

The train consists of an engine (@), followed by its carriages (o), and must collect magical fruits (*) which serve as fuel. The movement of the train follows these rules:

You will receive two parameters board and mov.

board is an array of strings that represents the board:

* `@` is the train's engine.
* `o` are the train's carriages.
* `*` is a magical fruit.
* `·` are empty spaces.

mov is a string that indicates the next movement of the train from the train's head @:

* `'L'`: left
* `'R'`: right
* `'U'`: up
* `'D'`: down.

  
With this information, you must return a string:

* `'crash*'`: If the train crashes into the edges of the board or itself.
* `'eat'`: If the train collects a magical fruit (*).
* `'none'`: If it moves without crashing or collecting any magical fruit.

Example:

```js
const board = ['·····', '*····', '@····', 'o····', 'o····']

console.log(moveTrain(board, 'U'))
// ➞ 'eat'
// Because the train moves up and finds a magical fruit

console.log(moveTrain(board, 'D'))
// ➞ 'crash'
// The train moves down and the head crashes into itself

console.log(moveTrain(board, 'L'))
// ➞ 'crash'
// The train moves to the left and crashes into the wall

console.log(moveTrain(board, 'R'))
// ➞ 'none'
// The train moves to the right and there is empty space on the right
```

### Solution (1/5 stars)

```js
function moveTrain(board, mov) {
  const engineRow = board.findIndex(row => row.includes('@'));
  const fruitRow = board.findIndex(row => row.includes('*'));
  const engineCol = board[engineRow].indexOf('@');
  const fruitCol = fruitRow !== -1 ? board[fruitRow].indexOf('*') : -1;

  const rows = board.length;
  const cols = board[0].length;

  switch (mov) {
    case 'U':
      if (engineRow === 0) {
        return 'crash'; 
      } else if (engineRow - 1 === fruitRow && engineCol === fruitCol) {
        return 'eat';
      } else if (board[engineRow - 1][engineCol] === 'o') {
        return 'crash'; 
      } else {
        return 'none'; 
      }

    case 'D':
      if (engineRow === rows - 1) {
        return 'crash'; 
      } else if (engineRow + 1 === fruitRow && engineCol === fruitCol) {
        return 'eat';
      } else if (board[engineRow + 1][engineCol] === 'o') {
        return 'crash'; 
      } else {
        return 'none'; 
      }

    case 'R':
      if (engineCol === cols - 1) {
        return 'crash'; 
      } else if (engineRow === fruitRow && engineCol + 1 === fruitCol) {
        return 'eat';
      } else if (board[engineRow][engineCol + 1] === 'o') {
        return 'crash'; 
      } else {
        return 'none'; 
      }

    case 'L':
      if (engineCol === 0) {
        return 'crash'; 
      } else if (engineRow === fruitRow && engineCol - 1 === fruitCol) {
        return 'eat';
      } else if (board[engineRow][engineCol - 1] === 'o') {
        return 'crash'; 
      } else {
        return 'none'; 
      }
  }
}
```
