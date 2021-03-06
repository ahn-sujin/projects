# CLOCK

### 구현기능
현재 시간(00:00:00)이 실시간으로 보여질 수 있도록 기능을 구현한다.

<br>

## Date and setInterval
```Date 객체```, ```Date 메소드```, ```setInterval메소드```를 이용하여 현재 시간을 구현한다. 

<br>

> index.html
```html

<h1 id="clock">00:00:00</h1>
<form id="login-form" class="hidden">
 <input
     required
     type="text"
     maxlength="15"
     placeholder="what is your name?"
 >
 <input type="submit" value="login">
 </form>

```
- 시계가 들어갈 자리를 잡아준다. ```<h1 id="clock"></h1>``` 

<br>

> clock.js

```javascript
const clock = document.querySelector('#clock')

function getClock(){
    const date = new Date();
    const hours = date.getHours()
    const minutes = date.getMinutes()
    const seconds = date.getSeconds()

    clock.innerText = `${hours}:${minutes}:${seconds}`
}

getClock();
setInterval(getClock, 1000);


```
- **Date 객체**
   - ```new Date()```  :  현재 날짜와 시간을 리턴한다.
- **Date.prototype 메소드** : ```Date``` 인스턴스는 Date.protype으로부터 메소드와 프로퍼티를 상속받는다. 
   - ```Date.prototype.getHours``` : 시간 표현(0~23) / 시간을 정수로 반환한다.
   - ```Date.prototype.getMinutes``` : 분 표현(0~59) / 분을 정수로 반환 한다.
   - ```Date.prototype.getSeconds``` : 초 표현(0~59) / 초를 정수로 반환 한다.

<hr>

- **setInterval(a,b)** : 매번(2초마다, 1분마다...) 일어나야하는 무언가를 나타낸다. 
   - a(첫번째 인자) : 실행하고자 하는 함수
   - b(두번째 인자) : 호출되는 함수를 몇 ms로 할지 
- **setTimeout(a,b)** : 일정시간 이후에는 실행한다.
   - a(첫번째 인자) : 실행하고자 하는 함수
   - b(두번째 인자) : 호출되는 함수를 몇 ms로 할지 
   
<br>

## padStart
**한 자리** 숫자를 **두 자리로** 표현한다. ``` 1 -> 01 ```

<br>

> clock.js
```javascript
const clock = document.querySelector('#clock')

function getClock(){
    const date = new Date();
    const hours = date.getHours().padStart(2,'0');
    const minutes = date.getMinutes().padStart(2,'0');
    const seconds = date.getSeconds().padStart(2,'0');

    clock.innerText = `${hours}:${minutes}:${seconds}`
}

getClock();
setInterval(getClock, 1000);

```
- **padStart(a,b)** : 앞쪽에 빈공간을 추가한다.
  - a(첫번째 인자) : 최대 길이 
  - b(두번째 인자) : 빈공간을 채울 문자
- **padEnd(a,b)** : 뒷쪽에 빈공간을 추가한다.
  - a(첫번째 인자) : 최대 길이 
  - b(두번째 인자) : 빈공간을 채울 문자 

<br>

### ☝ **padStart(padEnd)** 는 **String에서만 사용 가능**하고 Number에서는 사용이 불가능하다.

```javascript
const hours = String(date.getHours()).padStart(2,'0');
const minutes = String(date.getMinutes()).padStart(2,'0');
const seconds = String(date.getSeconds()).padStart(2,'0')

```
- Number를 String으로 바꿔서 호출할 때는
   - ```String()```을 사용해서 해당 부분을 감싸준다.

