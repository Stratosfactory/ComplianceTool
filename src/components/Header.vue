<template>
  <div>
      <div class="headingContainer"> <br>
      <img src="../assets/cloud.png">
      <h1>CHECKLIST CREATOR</h1>
      </div>
  </div>
</template>

<script>

export default {

}
</script>

<style scoped>
img{
  width: 100px;
  height: 100px;
 margin-left: 17%;
 align-self: left;
}
h1{
  justify-self: center;
  color:white;
  font-size: 40px;
  text-align:center;
  align-self: center;
  margin-left: 10px;
  
}
.headingContainer{
  width: 70%;
  border: 2px hsl(200, 35%, 45%) solid;
  margin:auto;
  display: flex;
  align-content: stretch;
  background-color:hsl(200, 55%, 15%);
  border-radius: 5px;
   -webkit-box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  -moz-box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  box-shadow: 0px 15px 20px 5px hsl(200, 55%, 25%);
  margin-bottom: 30px;
 

}
</style>