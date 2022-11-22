출처:	https://intrepidgeeks.com/tutorial/light-js-in-the-specific-box-you-click

**목표**

> 1. 클래스 .favorites_icon을 데이터로 갖는 변수를 만드세요.
> 2. 세 개의 박스 중 한 박스를 클릭하면 해당 박스가 노란색이 되도록 on 클래스를 추가하세요.
> 3. 단 하나의 박스가 노란색인 상태에서 다른 박스를 클릭하면 원래 노란색인 박스는 회색이 되도록 on 클래스를 제거하세요.

```javascript
const box = document.getElementsByClassName('.favorites_icon')
// const box = document.querySelectorAll('.favorites_icon'); 

/*
function onAndOff(event) {
    for(let i = 0; i < box.length; i++){
        event.target.classList.add('on');
    }
}
*/

function onAndOff(event) {
    for(let i = 0; i < box.length; i++){
        box[i].classList.remove('on');
    
        event.target.classList.add('on');
    }
}

for(let i=0; i < box.length; i++){
    box[i].addEventListener('click', onAndOff)
}
```

