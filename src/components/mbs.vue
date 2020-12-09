<template>
  <div class="card-columns">
    <div class="card m-2 w-100"
      v-for="cpu in cpusArr" 
      :key="cpu.id" 
    >
      <img src="../assets/logo.png" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{cpu.name}}</h5>
        <p class="card-text">{{cpu.attr}}</p>
      </div>
      <footer class="card-footer">
        <small class="text-muted">{{cpu.article}}</small>
      </footer>
    </div>
  </div>
</template>

<script>
import axios from "axios";
  export default {
    data() {
      return {
        cpusArr: []
      }
    },
    mounted () {
      let url = 'http://localhost:3456/MB'
      axios.get(url, 
        // {
        //   params: {
        //     _limit: 10
        //   }
        // }
      )
      .then(res => {
        this.cpusArr = res.data
      })
      .catch(function (error) {
        console.log(error);
      })
  },
  }
</script>

<style scoped>
.card {
  width: 250px;
  display: inline-block;
}
</style>