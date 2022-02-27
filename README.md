const readlineSync = require('readline-sync');
// let userName = readlineSync.question('May I have your name? ');
// console.log('Hello ' + userName);

d1 = `1. Столица Германии
a. Москва
b. Пекин
c. Берлин +`

d2 = `2. Какого цвета Елка
a. красная
b. розовая
c. зеленая +`

d3 = `3. Сколько планет в солнечной системе
a. 8 +
b. 17
c. 22`

let rightAnswer = 0
let wrongAnswer = 0
console.log(d1);
const otw1 = readlineSync.prompt();
if (otw1 === `c`) {
	rightAnswer++;
}
else {
	wrongAnswer++
}

 
console.log(d2);
const otw2 = readlineSync.prompt();
if (otw2 === `c`) {
	rightAnswer++;
}
else {
	wrongAnswer++
}

 
console.log(d3);
const otw3 = readlineSync.prompt();
if (otw3 === `a`) {
	rightAnswer++;
}
else {
	wrongAnswer++
}

console.log(`rightAnswer = ${rightAnswer}, wrongAnswer = ${wrongAnswer}`);
