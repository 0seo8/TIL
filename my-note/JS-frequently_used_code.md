# 자주 쓰는 코드

## Intro 

아직 입문단계인만큼 자바스크립트 코드를 작성하다보면, 뭔지 알것 같은데 잘 기억이 나지 않거나 이걸 이렇게 구현하는구나? 라고 느끼는 코드들이 많다.

오늘부터는 "아~" 싶은 코드는 적어놓고 반복 학습을 통해 어느순간 바로바로 튀어나오는 그 때 취소선을 긋는 식으로 공부를 해보려고 한다.

### contains('class-1')
```js
  const elClass = e.target.classList;
  if(!elClass.contains('active')) {
    items.forEach(
      item => item.classList.remove('active')
    )

```

### 가장 가까이 있는 id이름이 a인 요소 찾기
**closest()**
```js
cosnt StarRating = (e) => {
	e.target.closest('.a')
}
```

### data로 요소 찾기
**El.getAttribute('data-max-rating')**

```js
starRating.getAttribute('data-max-rating')
```

