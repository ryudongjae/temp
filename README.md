## 전환

전환은 효과가 변경되었을 때 부드럽게 처리해주는 CSS의 기능이다. 이와 관련된 것으로는 아래와 같은 속성들이 있다

```css
<!doctype html>
<html>
<head>
  <style>
    a{
      font-size:3rem;
      display:inline-block;
/*
      transition-property: font-size transform;
      transition-duration: 0.1s;
      transition:all 0.1s;
*/
      transition:all 0.1s;
    }
    a:active{
      transform:translate(20px, 20px);
      font-size:2rem;
    }
  </style>
</head>
<body>
  <a href="#">Click</a>
</body>
</html>
```

- transition-duration :전환 효과의 지속시간 설정 (기본값 : 0s)
- transition-property :전환 효과를 사용할 속성 이름 (기본값 : all)
- transition-delay : 전환 효과의 대기시간 설정 (기본값 : 0s)
- transition-timing-function :타이밍 함수 지정 (기본값 : ease)

## 애니메이션

CSS3 애니메이션은 요소에 적용되는 CSS 스타일을 다른 CSS 스타일로 부드럽게 전환시켜 줌

애니메이션은 애니메이션을 나타내는 CSS 스타일과 애니메이션의 중간 상태를 나타내는 keyframe들로 구성되어 진다.

그리고 애니메이션은 트랜지션보다 훨씬  규모가 크고 복잡하며 다양한 능력을 가지고 있기 때문에 좀 더 정밀한 효과를 구현할 수 있다.

- [animation-name] : `@keyframes`속성에서 설정한 애니메이션의 이름
- [animation-duration] : 애니메이션을 한 번 재생하는 데 걸리는 시간을 설정
- [animation-delay] : 애니메이션 시작을 지연할 시간을 설정
    - 0 : 속성을 적용하자마자 애니메이션을 시작한다(기본값).
    - now :속성을 적용하자마자 애니메이션을 시작한다. 0으로 설정한 것과 같다. iOS2.0부터 사용할 수 있다.
    - 숫자와 단위 : 설정한 시간이 지난 뒤에 애니메이션을 시작한다.

- [animation-direction] : 애니메이션 재생 방향을 정의하는 속성
    - normal : 애니메이션을 순방향으로 재생한다(기본값). 재생이 한 번 끝나면 첫 번째 프레임부터 다시 시작한다.
    - alternate : 순방향으로 애니메이션을 시작해 역방향과 순방향으로 번갈아 애니메이션을 재생한다. 홀수 번째로 재생할 때는 순방향으로 재생하고, 짝수 번째로 재생할 때는 역방향으로 재생한다.
    - reverse : 애니메이션을 역방향으로 재생한다. 재생이 한 번 끝나면 마지막 프레임부터 다시 시작한다.
    - alternate-reverse : 역방향으로 애니메이션을 시작해 순방향과 역방향으로 번갈아 애니메이션을 재생한다. 홀수 번째로 재생할 때는 역방향으로 재생하고, 짝수 번째로 재생할 때는 순방향으로 재생한다
- [animation-iteration-count] : 애니메이션을 재생하는 횟수를 정의하는 속성
    - 숫자 : 이며, 설정한 횟수만큼 애니메이션을 재생합니다.그리고 숫자가 소수면 애니메이션을 재생하는 도중에 첫 번째 프레임으로 돌아가 멈추고, 숫자가 음수면 애니메이션을 재생하지 않습니다.
        
        기본값은 1
        
    - infinite : 애니메이션을 무한으로 반복합니다.
    
- [animation-play-state] : 애니메이션 재생 여부를 정의하는 속성
    - running : 애니메이션을 재생한다(기본값).
    - paused : 애니메이션을 정지한다.
- [animation-timing-function] : 애니메이션의 키프레임 사이의 재생 속도를 조절하는 속성
- [animation-fill-mode]: 애니메이션이 시작되기 전이나 끝나고 난 후 어떤 값이 적용될지 지정

```css
.object { 
	animation-name: 1s; 
	animation-duration: 2s; 
	animation-delay: 1s; 
	animation-direction: alternate; 
	animation-iteration-count: 3; 
	animation-play-state: paused; 
	animation-timing-function: 1s; 
	animation-fill-mode: both; 
}
```

```css
div{
  position:absolute;
  left:200px;
  width:130px;
  height:60px;
  margin-left:-60px;
  background-color:#000;
  color:#fff;
  /* 애니메이션 이름 */
  animation-name: test;
  animation-duration:2s;
  animation-duration: leaner;
  animation-iteration-count:3;
  animation-direction:alternate;
  animation-fill-mode: forwards;
}

@-webkit-keyframes test {
  0% {
    left:100px;
  }
  100% {
    left:300px;
  }
}
```

키프레임

키프레임은 애니메이션을 적용할 요소을 정의하고 그 키프레임 코드 블럭에 재생할 프레임별 시간 비율을 작성

재생할 프레임별 시간 비율을 작성

- 0% : 애니메이션의 시작 프레임
- 100% : 애니메이션의 마지막 프레임
- from : 애니메이션의 시작 프레임이다. 0% 와 같다.
- to : 애니메이션의 마지막 프레임이다. 100% 와 같다.

```css
@keyframes test {
  0% {
    top:0px;
  }
  95% {
    width: 100px;
  }
  to {
    top:250px;
    width:85px;
    height:75px
  } 
}
```

## 다단(mutiple column)

텍스트 단을 column 속성으로 mutiple column으로 편집할 수 있습니다. mutiple column으로 편집한다는 의미는 어떤 레이아웃을 여러 개의 컬럼으로 쪼개서 구성한다는 것을 의미

****column–width 속성 →column-width는**** mutiple column ****구성 시 단의 너비를 지정하는 속성.****

```css
div { 
colum-width : 150px ; 
}
```

****column–count 속성 →column-count는**** mutiple column ****구성 시 단의 개수를 지정하는 속성.****

```css
div { 
column-count : 1 ; 
}
```

****columns 속성 →columns는 column의 너비와 개수를 일괄 지정하기 위한 대표 속성****

```css
div { 
columns : 150px 2 ;
 }
```

****column-rule 속성 →column-rule은 column과 column사이의 구분선을 표현하기 위한 속성****

```css
div { 
column-rule : #f00 solid 3px ; 
}
```

****column-gap 속성 →column-gap은 column과 column 사이의 간격을 지정하기 위한 속성****

```css
div { 
column-gap : 40px ; 
}
```

**column-span  속성**→ column-span은 mutiple column 구성 시 여러 단을 차지하는 요소를 지정하기 위한 속성

```css
div { 
column-span : all ; 
}
```

****column-fill 속성 → column-fill은**** mutiple column ****영역 콘텐츠 흐름의 영향을 받는 방식을 지정하는 속성****

```css
div { 
column-fill : balance ;
 }
```
