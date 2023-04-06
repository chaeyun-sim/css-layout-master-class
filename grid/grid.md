# Grid

- ******************************************grid-template-columns****************************************** : 열의 크기를 정한다. (행 길이)
    - 예) `grid-template-columns: 20px 55px 89px 100px;`
    - 그다음부터 column size가 지정되지 않았다면 밑으로 내려간다 (예를 들어 4 * 4)
    - size를 ********************auto 200px******************** 이렇게 한쪽을 auto로 맞춰주면 200px를 제외한 full-width가 된다.
    - width만 조정할 수 있음. height는 글자 크기
    
    
- ********************column-gap******************** : column 사이에 갭을 준다 (좌우)
  
    
- **************row-gap************** : row 사이에 갭을 준다 (상하)
    
- 혹은 row-gap column-gap 말고 그냥 gap으로 써도 된다.
- **********************************grid-template-row********************************** : 행의 크기를 정한다. (행 높이)
    
- 동일한 것을 여러개 만들때 : ********************************repeat(4, 200px) ⇒ grid-template-areas********************************
- 일정하지 않은 템플릿을 만들때 : ********grid-template-areas******** & ******************grid-area******************

  ```jsx
  .grid {
    display: grid;
    grid-template-columns: repeat(4, 200px);
    grid-template-rows: repeat(4, 200px);  // 이것도 그냥과 repeat을 섞어쓸 수 있다 (100px repate(2, 200px) 50px;
    **grid-template-areas**:     // 공간을 empty로 두고 싶다면 이름 대신에 .를 하면 된다.
    "header header header header"
    "content content content nav"
    "content content content nav"
    "footer footer footer footer";
  }

  .header {
    background: #2ecc71;
    grid-area: header;
  }

  .content {
    background: #3498db;
    grid-area: content;
  }

  .nav {
    background: #8e44ad;
    grid-area: nav;
  }

  .footer {
    background: #f39c12;
    grid-area: footer;
  }
  ```

- ******grid-column-start, grid-column-end******
    - 박스가 기준이 아닌 모서리가 기준이다 (gap)
    - 따라서 start 1 end 2를 해도 바뀌는 것은 없다. (1 2를 하면 첫번째 박스 자체니까)
        
        
- ****************************grid-row-start**************************** : row의 순서를 바꿀 수 있음.
    - 이것을 사용하면 위의 areas랑 같은 효과를 낼 수 있음.
    
    ```jsx
    .grid {
      display: grid;
      gap: 10px;
      grid-template-columns: repeat(4, 100px);
      grid-template-rows: repeat(4, 100px);
    }
    
    .header {
      background: #2ecc71;
      grid-column-start: 1;
      grid-column-end: 5;
    }
    
    .content {
      background: #3498db;
      grid-column-start: 1;
      grid-column-end: 4;
      grid-row-start: 2;
      grid-row-end: 4;
    }
    
    .nav { 
      background: #8e44ad;
      grid-row-start: 2;
      grid-row-end: 4;
    }
    
    .footer {
      background: #f39c12;
      grid-column-start: 1;
      grid-column-end: 5;
    }
    ```


## grid-column / grid-row

- grid-column-start / grid-column-end 말고 **grid-column: start number / end number** 로 작성하면 된다.
- 어디서부터 시작하고 끝나는지 보다는 얼마나 큰지를 적는게 좋다.
- 인덱스처럼 끝을 -1 -2 로 할 수 있다.
- cell이 너무 많을 경우는 start과 end를 적는 것이 힘들다. ⇒ 이건 cell 4개를 가지고 있어! ⇒ ************span 4************ 이라고 작성하면 된다.

## name columns or rows

```css
.grid {
  display: grid;
  gap: 10px;
  grid-template-columns: **[first-line] 100px [second-line] 100px [thired-line] 100px [forth-line] 100px [fifth-line];**
  grid-template-rows: repeat(4, 100px);
}

.header {
  background: #2ecc71;
	grid-column: first-line / fifth-line;
}
```

- repeat을 사용해서 쓰려면 ********************************************************repeat(4, 100px [new-line])******************************************************** 이런식으로 쓰면 된다.
- 사용 방법 : `grid-row: new-line 1 / new-line 3;`

## Fr. (fraction)

- `grid-template-columns: repeat(4, 1fr);`
- full-width 같은 느낌 (페이지만큼 가로로 가득 채움) (비율? 같음)
    
- `4fr 1fr 1fr 1fr`
  | ---- | - | - | - |
    
- grid에 height를 작성해주지 않으면 row에 1fr을 해도 아무것도 나타나지 않는다.

## grid-template

- div에 이름을 지정해주고 그 이름으로 row마다 height을 바꿀 수 있음

  ```jsx
  .grid {
    display: grid;
    gap: 10px;
    height: 50vh;
    grid-template:
    "header header header header" 1fr
    "content content content nav" 2fr
    "footer footer footer footer" 1fr / 1fr 1fr 1fr 1fr (각각의 width)
  }

  .header {
    background: #2ecc71;
    grid-area: header;
  }

  .content {
    background: #3498db;
    grid-area: content;
  }

  .nav { 
    background: #8e44ad;
    grid-area: nav;
  }

  .footer {
    background: #f39c12;
    grid-area: footer;
  }
  ```

- row에 이름을 붙일 수도 있음

```jsx
grid-template:
  [header-start] "header header header header" 1fr [header-end] 
  [content-start] "content content content nav" 2fr [content-end] 
  [footer-start] "footer footer footer footer" 1fr  [footer-end] / 1fr 1fr 1fr 1fr
  ;
```

- grid-template에서는 repeat 사용할 수 없음
- fr을 사용하면 %를 사용한 것 처럼 browser width를 늘리거나 줄여도 비율은 같음.

## justify-items

- ********stretch******** : (기본) 자식들을 늘려서 width를 전부 채우게 한다.
- ************************************start, center, end************************************ : div의 글자만큼 width가 정해지고 해당 섹션의 왼쪽, 중앙, 오른쪽에 위치한다.

## align-items

- justify-items과는 vertically 같다.