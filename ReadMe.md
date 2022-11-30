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
