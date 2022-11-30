코지코더 - 뷰js 2 (vuejs 2) 기초 익히기 기본 강좌

https://youtu.be/gZBKGn0wQXU

---

1. 뷰 인스턴스 생성

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

2. 데이터 바인딩

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

3. 이벤트  
   뷰 공식 페이지, 이벤트 수식어 : https://v2.vuejs.org/v2/guide/events.html#Event-Modifiers

   ```
    1. 이벤트 앞에 'on' 삭제, 'v-on:' 추가
    <button v-on:click="클릭이벤트js">버튼명</button>

    2. 이벤트 앞에 'on' 삭제, '@' 추가
    <button @click="클릭이벤트js">버튼명</button>
   ```

4. 데이터 양방향 바인딩 (Data Two Way Binding - v-model)  
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

5. [Computed 속성](https://v2.vuejs.org/v2/guide/computed.html)  
   템플릿안에 간단한 연산을 넣는 건 괜찮지만, 너무 많은 연산을 하려고 하면 코드가 비대해지고 유지보수가 어렵다.  
   이런 경우 computed 속성을 사용해보자.

   Computed VS Method?

   - **computed 속성은 캐싱을 하고 method 속성은 캐싱을 하지 않는다.**
     - computed는 data 속성에 변화가 있을때 자동으로 다시 연산을 한다.  
       같은 페이지내에서 같은 연산을 여러번 반복해야 할 경우에 성능면에서 효율적으로 사용할 수 있다.
     - methods는 캐싱이라는 개념이 없기 때문에 매번 재 렌더링된다.

6. [Watch 속성](https://v2.vuejs.org/v2/guide/computed.html#Watchers)  
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

7. [클래스 & 스타일 바인딩](https://v2.vuejs.org/v2/guide/class-and-style.html)
   data속 불린타입 변수값만 바꿔도 remove/add class가 가능하다.
