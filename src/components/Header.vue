<template>
  <div>
      <div class="headingContainer">
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

 align-self: left;
}
h1{
  
  color:white;
  font-size: 40px;
  text-align:end;
  
  margin-left: 40px;
  
}
.headingContainer{
  width: 70%;
  border: 2px hsl(200, 35%, 45%) solid;
  margin:auto;
  display: flex;
  align-content:center;
  align-items: center;
  justify-content:center;
  justify-items: center;
  background-color:hsl(200, 55%, 15%);
  border-radius: 5px;
   -webkit-box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  -moz-box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  box-shadow: 0px 15px 20px 5px hsl(200, 55%, 25%);
  margin-bottom: 30px;
 

}
</style>