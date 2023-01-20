<!--단방향 바인딩-->

<template>
    <div :class="nameClass">
<!--    {{greeting(name)}}-->
<!--      {{greet}}-->
<!--      {{greeting('name')}}-->
<!--      {{objectName}}-->
      {{name}}
    </div>

<!--  <button class="btn btn-primary"-->
<!--          v-on:click="consoleLog">Click</button>-->

  <input :type="type" :value="name">
  <button class="btn btn-danger"
          @click="updateName">updateName</button>
<!--  v-bind = : -->
<!--  v-on = @ -->
<!--  한 태그안에 다섯개까지만-->
</template>

<script>
import { ref,reactive } from 'vue';
export default {
  setup(){
    //변수,함수 선언
    const type = ref('text');
    //타입 작성 number , text..
    const name = ref('네임');
    const nameClass = ref('');
    const objectName = reactive({
      id : 1
    })
    //기본 자료형(숫자,문자)은 ref
    //object,array는 reactive
    const greeting = (name) => {
      return 'hello' + name;
    }
    const greet = greeting(name);
    // 두 변수는 같은 내용이다

    const consoleLog = () => {
      console.log('hello world');
    };

    const updateName = () => {
      name.value = "i wanna go home"
      //ref 사용할때는 .value 사용
      //objectName.id = 2;
      //reactive 사용할때는 value안적어도 됨
      type.value = 'text';
      //넘버선언 -> 텍스트 데이터 바인딩
      nameClass.value='name';
      console.log(name);
    };

    return{
      name,
      greeting,
      greet,
      consoleLog,
      updateName,
      objectName,
      type,
      nameClass
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.name {
  color: red;
}
</style>
