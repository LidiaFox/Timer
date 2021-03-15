## TIMER
Установить правильную дату окончания
Высчитать оставшееся время
Привести дату к удобному формату
Вывести данные таймера, как многоразовый объект
Отобразить часы на странице и остановить их, когда они достигнут нуля


#### Setting deadline
`let deadline = 'April 01 2021 00:00:00';`

#### Calculalte the remaining time

`function getTimeRemaining(endtime)`

Pass an argument to the function `endtime` - it is our the deadline.
Create variable will calculalte remaining time. For this we use metod `parse()` - it converts date to namber of milliseconds. And subtract "date now" (new Date).

`let t = Date.parse(endtime) - Date.parse(new Date())`


After this, **I get seconds, minutes and hours**. I use metod `Math.floor` to take integers. I divide by 1000 to get seconds(1 second = 1000 millisekonds) and I get the remaining of the division by 60 (numbers is minute, if it more than 60). I do with the rest by analogy.

`seconds = Math.floor((t/1000) % 60)`

And this function return object, that I create directly in it.

`'total'` - key `'t'` - value.

#### Dinamic

`function setClock(id, endtime)`

This function create dinamic. It writes our data in DOM and updated them.

First argument to the function `id` - it is finds an element where to write, second the `endtime`.

For start I get elements from DOM.

`timer = document.getElementById(id)`
I pass argument this same `id` to this metod, in order to get the rest.
 I get remaining elements use `querySelector`.
`hours = timer.querySelector('.hours')`


Becouse I need to **updated datas**, that  I wrote down, every second, I create a new function in this function.

`function updateClock()`


I use function `getTimeRemaining` to get our object and data from it. And I use metod `innerHTML` to write data. If the number is less than 10, I want to see "0" before it. For this I add string '0' before it and use metod `slice`.

`minutes.innerHTML = ('0' + t.minutes).slice(-2)`

I use metod `setInterval`, to the function run every second. And I write it to variable `timeInterval` to function setClock.

`timeInterval = setInterval(updateClock, 1000)`

First argument is function `updateClock`, because I am update the recorded data. Second argument is time after which it is update. It is measured in millisekonds.

And I need to stop my timer, when it will be = deadline. I use `if`

` if (t.total <= 0)`

and metod clearInterval, in which I pass argument our `timeInterval`

`clearInterval(timeInterval)`

At the end I run the function with arguments `'timer'` and `deadline`.

`setClock('timer', deadline)`