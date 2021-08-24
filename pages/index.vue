<template>
  <div>
    <h1>Check: {{ apiValue }}</h1>
    <button @click.prevent="testBackendRequest">Request API</button>
    <Tutorial/>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data(){
    return {
      apiValue: ''
    }
  },

  mounted(){
    // this.testBackendRequest();
  },

  methods:{
    testBackendRequest() {
      this.$axios.get('/test').then(res => {
        // console.log(res.data);
        this.apiValue = res.data;
      });
    }
  },
  

});
</script>
