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