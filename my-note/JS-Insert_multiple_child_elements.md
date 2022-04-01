# 자식요소 여러개 삽입하기.

## Intro

지난 번에 비슷한 구조의 코드를 작성해보았지만, 아직 익숙지가 않아 따로 포스팅을 해 정리를 해보았다.

**html**
```
...
<div class="star-rating" data-max-rating="5"></div>
(...)
<div class="star-rating" data-max-rating="4"></div>
(...)
<div class="star-rating" data-max-rating="2"></div>
(...)

```

`data-max-rating`의 값만 `.star-rating`요소가 여러개 있다고 가정할 때, 이 `.star-rating`하부 요소에 `data-max-rating`의 값만큼의 `<i class="star"></i>`를 삽입하고자 할 때 코드를 어떻게 작성해야할까?

**js**
```js
const starRatng = document.querySelectorAll('.star-rating');
const maxRating = starRating.getAttribute('data-max-rating');

const newNode = document.createDocumentFragment();
  
for(let i = 0; i<maxRating; i++) {
    const star = document.createElement('i')
    star.classList.add('star')
    newNode.appendChild(star)
  }

$container.appendChild(newNode)
```

## 필요한 기본 배경
참고 : [MDN](https://developer.mozilla.org/ko/docs/Web/API/DocumentFragment)
### 1. Document.createDocumentFragment()
- 새로운 빈 `DocumentFragment`를 생성한 후 반환합니다. 여기서 `DocumentFragment`란, 부모가 없는 아주 작은 document 객체를 나타냅니다. 아래 그림을 참고하면 조금 더 이해가 쉽습니다.
![](https://media.vlpt.us/images/0seo8/post/2c5d2879-2bde-4b92-a4ed-6cb2c272edd5/image.png)


### 2. getAttribute() : 요소의 data속성 값을 찾
- 해당속성에 지정된 값을 반환합니다.

