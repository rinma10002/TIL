# CSS Layout
- 각 요소의 **위치**와 **크기를 조정**하여 웹페이지의 디자인을 결정하는 것

# CSS Box Model
- 웹 페이지의 모든 HTML 요소를 감싸는 사각현 상자 모델
### 박스 구성 요소
- Margin : 이 박스와 다른 요소 사이의 공백
- content : 콘텐츠가 표시되는 영역, width 와 height 속성을 사용하여 크기 조정
- Border : 콘텐츠와 패딩을 감싸는 테두리 영역
- Padding : 콘텐츠 주위에 위치하는 공백 영역
### shorthand 속성
- border : border-width, border-style, border-color 를 한번에 설정하기 위한 속성
    - ex) border: 2px solid black (작성 순서는 영향을 주지 않음)
- margin & padding : 4방향의 속성을 각각 지정하지 않고 한번에 지정할 수 있는 속성
    - 4개 상우하좌  
    margin: 10px 20px 30px 40px;  
    padding: 10px 20px 30px 40px;
    - 3개 상/좌우/하  
    margin: 10px 20px 30px 40px;  
    padding: 10px 20px 30px 40px;
    - 2개 상하/좌우  
    margin: 10px 20px 30px 40px;  
    padding: 10px 20px 30px 40px;
    - 1개 공통  
    margin: 10px 20px 30px 40px;  
    padding: 10px 20px 30px 40px;
### box-sizing 속성
- 실제 박스 크기는 컨텐츠 박스 + 패딩 + 태두리
- 하지만 **box-sizing 속성** 을 사용하여 실제 박스 크기를 정해주면, 따로 태두리와 패딩을 조정할 필요가 없음
     ```html
        * {
        box-sizing: border-box;
        }
    
### 기타 display 속성
1. inline-block
    - 요소가 줄바꿈 되는 것을 원하지 않으면서 너비와 높이를 적용하고 싶은 경우에 사용
    ```html
        .box {
            display: inline-block;
            width: 100px;
            height: 100px;
            background-color: blaxk;
            margin: 10px;
        }
2. none
    - 요소를 화면에 표시하지 않고, 공간조차 부여되지 않음
    ```html
        .none {
            display: none;
        }

# CSS Position
- 요소를 Normal Flow에서 제거하여 다른 위치로 배치하는 것
- 목적 : 전체 페이지에 대한 레이아웃을 구성하는 것보다는 페이지 특정 항목의 위치를 조정하는 것
### Position 유형
1. static
    - 요소를 Normal Flow에 따라 배치
    - 기본값
2. relative
    - 요소를 Normal Flow에 따라 배치 
    - 자신의 원래 위치를 기준으로 이동
3. absolute
    - 요소를 Normal Flow에서 제거
    - 가장 가까운 relative 부모 요소를 기준으로 이동
    - 문서에서 요소가 차지하는 공간이 없어짐
4. fixed
    - 요소를 Normal Flow에서 제거
    - Viewpoint 를 기준으로 이동
    - 스크롤해도 항상 같은 위치에 유지됨
    - 문서에서 요소가 차지하는 공간이 없어짐
5. sticky
    - relative 와 fixed 의 특성을 결합한 속성
    - 스크롤 위치가 임계점에 도달하기 전에는 relative처럼 동작
    - 스크롤이 특정 임계점에 도달하면 fixed 처럼 동작하여 화면에 고정됨
    - 만약 다음 sticky 요소가 나오면 다음 sticky 요소가 이전 sticky 요소의 자리를 대체
### z-index
1. 요소의 쌓임 순서를 정의하는 속성
2. 정수 값을 사용해 Z축 순서를 지정
3. 값이 클수록 요소가 위에 쌓이게 됨
4. static이 아닌 요소에만 적용됨


# CSS Flexbox
- 요소를 행과 열 형태로 배치하는 1차원 레이아웃 방식
- 박스 Display 타입 중, Inner display type
    ```html
        .container {
            display: flex;
        }
- 박스 내부의 요소들이 어떻게 배치될지를 결정
- 속성 : flex
### Flexbox 구성 요소
- Flex Container
- Flex Item
- main axis
- cross axis
### Flexbox 속성
1. Flex Container 관련 속성
    - display, flex-direction, flex-wrap, justify-content, align-items, align-content
2. Flex Item 관련 속성
    - align-self, flex-grow, flex-basis, order
3. 참고
    - justify-items 및 justify-self 속성이 없는 이유
        - margin auto 를 통해 정렬 및 배치가 가능하기 때문에
### Flex-wrap 응용

# 참고
### 마진 상쇄
### 박스 타입 별 수평 정렬
### 실제 Position 활용 예시
### Flexbox Shothand 속성
### Flexbox 속성 정리