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