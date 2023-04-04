### block

- box 개념
- 너비와 높이를 가짐
- 오른쪽 끝까지 margin이 있음
- element가 한 줄을 차지하여 옆에 다른 element가 올 수 없어 아래로 배치

<br />

### inline

- 같은 직선 상에 있다는 뜻으로 옆에 다른 element가 올 수 있음
- box가 아니라 너비와 높이를 가질 수 없음
- element contents에 따라 유동적

<br />

### inline-block

- inline과 block의 속성을 모두 지님
- element가 일직선 상에 배치되어 옆에 다른 element가 올 수 있음
- 너비와 높이를 가질 수 있음
- 단 element 사이에 정체불명의 margin(gap)이 생겨 layout을 계산해야하는 불편함이 있음

<br />

### flexbox

- inline-block의 문제점을 해결한 방식
- children에 직접적인 컨트롤 X
- `flexbox container` : box를 싸고 있는 div에 **************************display: flex************************** 를 해준다. (inline-block 과 동일함)
- 바로 위의 부모가 자식의 위치를 결정할 수 있음. (바로 위의 div이 아닌 다른 div에 flex를 해둔다고 자식이 flex가 적용되지는 않음)
- MUST BE INSIDE

<br />

### flex-direction

- row : 가로 정렬 (기본)
    - main axis : 가로
    - cross axis : 세로
- column : 세로 정렬
    - main axis : 세로
    - cross axis : 가로

<br />

### justify-content

- main axis 방향으로 item을 옮김.
- **center**: 모든 요소를 중앙 정렬
- **end**: 모든 요소를 끝 정렬 (제일 오른쪽)
- **left** 또는 **right** : 모든 요소를 왼쪽/오른쪽에 정렬
- **space-around** : 모든 요소의 양 옆에 동일한 margin을 준다 (1 - box - 1 - 1 - box - 1 - 1 - box - 1)
- **space-between** : 요소의 사이에만 동일한 margin을 준다. (첫번쨰와 마지막은 가장자리에 붙는다)
- **space-evenly** : 요소의 사이와 끝에 동일한 margin을 준다 (1 - box - 1 - box - 1 - box  - 1)

<br />

### align-item

- cross axis 방향으로 item을 옮김.
- **center** : 모든 요소를 중앙 정렬 (아무것도 바뀌지않았을때 height를 추가해보자 (flexbox container))
- **************stretch************** : children에 height가 없으면 full-height
- ****************flex-end****************  : 제일 아래에 정렬
- ********flex-start******** : 제일 위에 정렬 (기본)

### children을 직접 움직이게 하는 요소들

### align-self

- align-items와 비슷함
- children이 아닌 child 하나만 적용된다.
- `부모 css에 height가 있어야만 적용됨`
- ************center************ : 중앙 정렬
    
    
- ****************flex-end**************** : 아래 정렬
    

### order

- html을 수정할 필요 없이 순서를 바꿀 수 있다.
- **************************************order: 자리 수**************************************
- 예) 1 - 2 - 3 으로 정렬되어있을 때

```jsx
.child:nth-child(1){
	order: 2;   // 1번은 두번째 자리로
}

.child:nth-child(2){
	order: 2;  // 2번은 원래 2번째 자리이지만 1번이 이미 두번째 자리에 와있기 때문에 3번이 됨.
}

// 그리고 3번은 원래 3번째 자리이지만 2번이 세번째 자리에 와있기 때문에 1번이 됨.
```

### flex-wrap

- 여러개의 박스가 한줄에 있을 때 width는 제역할을 못할수도 있다.
- **********flex-wrap: wrap********** : 각각에 미리 지정한 width를 부여함 (mui Box sx={} sm={} 과 같음)
    
- ********************flex-wrap: wrap-reverse******************** : wrap한 상태에서 마지막 div부터 순서대로 나타나게 해줌.
    
- father에 정의해줌


### flex-direction

- father에 정의해줌

- **********************row-reverse********************** : 마지막 div부터 가로로 차례대로 출력한다.
    
- ******column-reverse****** : 마지막 div부터 세로로 차례대로 출력한다.
    

### align-content

- wrap 된 상태로 align-content를 하면 (father) 중간의 line이 없어진다.

- father에 정의해줌

- ********************flex-start******************** : 중간의 선이 없어지고 모든 div가 위로 정렬되었다.

- ************center :************ 중앙 라인이 없어지고 모든 div가 중앙 정렬 되었다.
    
- **************************space-between************************** : 절반은 위로, 절반은 아래로 간다.
    
    

### flex-shrink

- father의 flex-wrap이 nowrap 일때 특정 div만 줄어들게 할 수 있다.

- child에 정의해줌

### flex-grow

- father의 flex-wrap이 nowrap 일때 특정 div만 늘어나게 할 수 있다/

- child에 정의해줌
    

### flex-basis

- div가 찌그러지거나 늘어나기 전에 initial width를 설정해주는 것
- child에 지정함 (father에 height나 width(direction: column일때)가 있어야한다.)