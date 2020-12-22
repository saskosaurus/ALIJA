<template>

  <div class="home">

    <div class="container">
      <div class="row">
        <div class="col-sm">
          
        </div>
        <div class="col-sm">
          
          <div class="jumbotron">
            <h1 class="display-4">Dobrodosli u HR ALIAS</h1>
            <p class="lead">This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.</p>
            <hr class="my-4">
            <p>It uses utility classes for typography and spacing to space content out within the larger container.</p>
            <p class="lead">
              <router-link to="/newGame"><a class="btn btn-primary btn-lg" href="#" role="button">Pokreni igru</a> </router-link>
              <router-link to="/options"><a class="btn btn-primary btn-lg" href="#" role="button">Opcije</a> </router-link>
            </p>
          </div>


        </div>
        <div class="col-sm">
         
        </div>
      </div>
    </div>



    

  </div>
  
</template>

<script>



export default {
  name: 'Home',
  components: {
    
  }
}
</script>


<style>





</style>