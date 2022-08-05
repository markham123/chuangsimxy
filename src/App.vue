<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <div>
      <button v-for="(item,index) in buttons" :key="index" @click="selectButton(index)">{{item}}</button>
    </div>
    <div>选择了【{{selected}}】</div>
    <Suspense>
      <template #default>
        <ajaxGet></ajaxGet>
      </template>
      <template #fallback>
        <h1>loading</h1>
      </template>
    </Suspense>
  </div>
</template>

<script lang="ts">
import { defineComponent,ref,reactive,toRefs,watch } from 'vue';
import ajaxGet from './components/ajaxGet.vue';

export default defineComponent({
  name: 'App',
  components:{ ajaxGet },
  setup () {
    const data = reactive({
      buttons:['小明','小红','小军'],
      selected:'',
      selectButton:(index:number) => {
        data.selected = data.buttons[index]
      }
    })
    const refData = toRefs(data)
    watch(()=>data.selected,(newValue,oldValue)=>{
      console.log(newValue,oldValue)
      
    })
    // const buttons = ref(['小明','小红','小军'])
    // const selected = ref('')
    // const selectButton = (index:number)=>{
    //   selected.value = buttons.value[index]
    // }
    // return{
    //   buttons,selected,selectButton
    // }
    return{
      ...refData
    }
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
