<template>
    <div class="skard">   
      <div class="card">
        <router-link to="/">
            <div class="card-header text-left">
                <img src="soap.png">
            </div>
        </router-link>
        <div class="card-footer text-muted text-left">
            SAPUN 15kn
        </div>
      </div>
    </div> 
    

</template>

<script>
export default {
  name: 'proizvod',
  props:  ["info"]
}
</script>

<style lang="scss">
.card{
    margin:20px;
    background-color:transparent;
    
}

.skard{
  .card:hover{
  transition:0.5s;
  background-color:white;
  opacity:0.6
}
}



</style>
