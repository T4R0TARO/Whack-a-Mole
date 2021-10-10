
```js
/*
* Contain all the elements in a variable for later use
*/
const squares = document.querySelectorAll('.square')
const mole = document.querySelector('.mole')
const timeLeft = document.querySelector('#time-left')
const score = document.querySelector('#score')

let result = 0
let hitPosition
let currentTime = 60
let timerId = null
```

```js
/*  Add mole class to random square 
*   loop through the items within the squares array and remove the mole class
*   Do this just to clear any left behind classes
*   create randomSqaure variable that create a random number out of 9
*   The random number will add the mole class
*   hitPosition will equal the randomSquare's id
*/
function randomSquare() {
    squares.forEach(square => {
      square.classList.remove('mole')
    })
  
    let randomSquare = squares[Math.floor(Math.random() * 9)]
    randomSquare.classList.add('mole')
  
    hitPosition = randomSquare.id
  }
```

```js
// each square add eventlistener if square if match hitPosition add to results
/* loop through the items of the squares array and addEventListener with type 'mousedown'
*  if the use mousedown the square.id  with the hitPosition mole add to result
*   change the textContent of score to equal the new results
* hitPosition = null?
*/
square.forEach(square => {
    square.addEventListener('mousedown', () => {
        if(square.id == hitPosition){
            result++
            score.textContent = result
            hitPosition = null
        }
    })
})
```

```js
// move mole to randomSquare every 500ms
// timerId will be set fire randomSquare function every 500ms
function moveMole() {
    timerId = setInterval(randomSquare, 500)
}

moveMole()
```

```js
//countdown
function countDown() {
    currentTime--
    timeLeft.textContent = currentTime

    if( currentTime = 0){
        clearInterval(countDownTimerId)
        clearInterval(timerId)
        alert(`GAME OVER! Your final score is ${result}`)
    }
}
//timer count down
let countDownTimerId = setInterval(countDown, 1000)
```