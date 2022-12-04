코지코더 - 뷰js 2 (vuejs 2) 기초 익히기 기본 강좌

https://youtu.be/gZBKGn0wQXU

---

1.  뷰 인스턴스 생성

    1. index.html 생성
    2. title 태그 하단에 개발용 vue 스크립트 추가
       ```
           <script src="https://cdn.jsdelivr.net/npm/vue@2.7.13/dist/vue.js"></script>
       ```
    3. body 태그 하단에 추가

       ```
       <script>
         new Vue({
             el : 타겟 ID
             data : {
                 // 타겟 태그 내에서 사용할 데이터
             }
             methods : {
                 // 타겟 태그 내에서 사용할 메소드 정의
                 함수명(){

                 },
                 함수명 : function() {

                 }
             }
         })
       </script>
       ```

2.  데이터 바인딩

    - body 태그 내 사용

    ```
     <body>
         {{person.name}} //뷰 스크립트에서 정의한 데이터명
         {{nextYear()}}  //뷰 스크립트에서 정의한 함수명
     </body>
    ```

    - 태그 내 데이터 바인딩

    ```
    // 1. 바인딩 할 속성 앞에 'v-bind:' 추가 후, 속성값에 데이터명 작성
    <input v-bind:type="type" v-bind:value="inputData" />

    //2. 바인딩 할 속성 앞에 ':' 추가 후, 속성값에 데이터명 작성
    <input :type="type"  d:value="inputData" />
    ```

3.  이벤트  
    뷰 공식 페이지, 이벤트 수식어 : https://v2.vuejs.org/v2/guide/events.html#Event-Modifiers

    ```
     1. 이벤트 앞에 'on' 삭제, 'v-on:' 추가
     <button v-on:click="클릭이벤트js">버튼명</button>

     2. 이벤트 앞에 'on' 삭제, '@' 추가
     <button @click="클릭이벤트js">버튼명</button>
    ```

4.  데이터 양방향 바인딩 (Data Two Way Binding - v-model)  
    **v-model** 을 사용하면 됨!

    ```
     <div id="app">
         // input에 데이터 입력하면 실시간으로 변경된 text 데이터 출력됨.
         <input type="text" v-model="text"/><br />
         {{text}}<br/>
       </form>
     </div>
     <script>
       new Vue({
         el: "#app",
         data: {
           text: "text",
         },
         methods: {
         },
       });
     </script>
    ```

5.  [Computed 속성](https://v2.vuejs.org/v2/guide/computed.html)  
    템플릿안에 간단한 연산을 넣는 건 괜찮지만, 너무 많은 연산을 하려고 하면 코드가 비대해지고 유지보수가 어렵다.  
    이런 경우 computed 속성을 사용해보자.

    Computed VS Method?

    - **computed 속성은 캐싱을 하고 method 속성은 캐싱을 하지 않는다.**
      - computed는 data 속성에 변화가 있을때 자동으로 다시 연산을 한다.  
        같은 페이지내에서 같은 연산을 여러번 반복해야 할 경우에 성능면에서 효율적으로 사용할 수 있다.
      - methods는 캐싱이라는 개념이 없기 때문에 매번 재 렌더링된다.

6.  [Watch 속성](https://v2.vuejs.org/v2/guide/computed.html#Watchers)  
    watch 속성은 데이터 변화를 감지하여 자동으로 특정 로직을 수행한다.  
    computed 속성과 유사하지만 computed는 내장 api를 사용하는 간단한 연산정도에 적합하고  
    watch는 데이터 호출과 같이 시간이 상대적으로 더 많이 소모되는 비동기 처리에 적합하다.

    ```
    watch: {
     //데이터명과 함수명이 동일해야함.
     message(newValue, oldVal) { // 새로운 값, 이전 값
         console.log(newValue, oldVal);
         ...
       },
     },
    ```

    참고글) [계산된 속성(computed), 감시자(watch)](http://hong.adfeel.info/frontend/%EA%B3%84%EC%82%B0%EB%90%9C-%EC%86%8D%EC%84%B1computed-%EA%B0%90%EC%8B%9C%EC%9E%90watch/)

7.  [클래스 & 스타일 바인딩](https://v2.vuejs.org/v2/guide/class-and-style.html)
    data속 불린타입 변수값만 바꿔도 remove/add class가 가능하다.

8.  v-if, v-show

    - v-if : v-if를 사용하여 조건에 따른 조건부 렌더링이 가능하다.
    - v-show : v-show를 사용하여 조건에 따라 렌더링 된 태그의 display를 설정 할 수 있다.

    |                           | v-if                        | v-show               |
    | ------------------------- | --------------------------- | -------------------- |
    | 렌더링                    | false일 때 렌더링 하지 않음 | 무조건 렌더링        |
    | 조건에 부합하지 않는 경우 | false일때 DOM에서 사라짐    | display:none; 처리됨 |

9.  [v-for](https://v2.vuejs.org/v2/guide/list.html)  
     배열, 객체 모두 사용 가능 (주로 배열 사용..~)

    ```
    <div v-for="(배열값, 배열인덱스) in 배열" :key="배열값마다 가지고 있는 고유한 값">
       {{배열값.name}} {{배열값.age}}
    </div>
    ```

10. 여러개의 Vue 인스턴스 사용하기

    1. new Vue({...})로 생성한 인스턴스를 변수에 담아준다.
    2. 하나 더 만듬
    3. Vue 인스턴스에서 다른 Vue 인스턴스의 데이터 혹은 메소드의 접근 하고 싶을 때  
        '인스턴스 변수명.데이터명, 인스턴스 변수명.메소드명' 이런 식으로 접근 할 수 있다.

       ```
       <script>
        const app = new Vue({
          el: "#app",
          data: {
            name: "soom",
          },
          methods: {
            changeText() {
              app1.name = "soom updated"; //***
            },
          },
        });
        const app1 = new Vue({
          el: "#app-1",
          data: {
            name: "soom1",
          },
          methods: {
            changeText() {
              app.name = "soom1 updated"; //***
            },
          },
        });
       </script>
       ```

11. [Vue 컴포넌트](https://v2.vuejs.org/v2/guide/components.html)

    1.  전역 등록 : 어떤 vue 인스턴스에서도 사용할 수 있음. 스크립트 내 Vue.component를 만든다.

        ```
        Vue.component('컴포넌트명', {

        template : `렌더링 시킬 HTML element 작성`,
          data() {
            //data가 객체(배열)인 경우 참조형 데이터이므로 data가 변형되지 않기 위해
            //data()함수로 작성
            return obj;
          },
          methods: {
            ...
          },
        })
        ```

    2.  지역 등록 : 전역 컴포넌트 인 경우 더 이상 사용하지 않는 컴포넌트이여도 최종 빌드에 들어가게 되므로 자바스크립트의 양이 불필요하게 커질 수 있다.  
        **이러한 것을 막기 위해 지역 컴포넌트를 사용해보자**

        1. 컴포넌트를 생성하여 변수에 담는다.
        2. 뷰 인스턴스를 생성할 때, 사용할 컴포넌트를 함께 등록해준다.
           ```
            const app = new Vue({
              el: "#app",
              components: {
                "soom-button": SoomButton,
              },
            });
           ```

12. vue cli 설치

    1. node js lts 버전 설치
    2. yarn global add @vue/cli 입력
    3. 설치 완료 확인 : vue --version
    4. 뷰 설치 : vue create hello-world
    5. vue cli를 설치 하지 않고, vue를 설치하고 싶다면? @vue/cli create test2
