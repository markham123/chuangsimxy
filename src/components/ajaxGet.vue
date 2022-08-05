<template>
  <div>
    <h1>{{result}}</h1>
  </div>
</template>

<script>
  export default {
    setup() {
      return new Promise((resolve,reject)=>{
        setTimeout(() => {
          resolve({result:'sadasdasd'})
        }, 2000);
      })
    }
  }
</script>

<style lang="scss" scoped>

</style>