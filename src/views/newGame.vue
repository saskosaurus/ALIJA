<template>
  <div class="about">

    <div class="container">
      <div class="row">
        <div class="col-sm">
          
        </div>
        <div class="col-sm">
          
          <label for="exampleInputEmail1">Broj igraca</label>
          <br>
          4<input type="radio" name="rating" id="rating-5" value="4" v-model="numberPlayer"> 
          6<input type="radio" name="rating" id="rating-5" value="6" v-model="numberPlayer"> 
          8<input type="radio" name="rating" id="rating-5" value="8" v-model="numberPlayer"> 
          10<input type="radio" name="rating" id="rating-5" value="10" v-model="numberPlayer"> 

          <form> <!-- forma za dodavanje igraca-->

            <div class="form-group" v-if="numberPlayer>=4">
              <label for="exampleInputEmail1">Tim 1</label>
              <input type="text" v-model="playerOne" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <div class="form-group" v-if="numberPlayer>=4">
              <input type="text" v-model="playerTwo" class="form-control" id="exampleInputEmail2" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <div class="form-group" v-if="numberPlayer>=4">
              <label for="exampleInputEmail1">Tim 2</label>
              <input type="text" v-model="playerThree" class="form-control" id="exampleInputEmail3" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <div class="form-group" v-if="numberPlayer>=4">
              <input type="text" v-model="playerFour" class="form-control" id="exampleInputEmail4" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <div class="form-group" v-if="numberPlayer>=6">
              <label for="exampleInputEmail1">Tim 3</label>
              <input type="text" v-model="playerFive" class="form-control" id="exampleInputEmail5" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <div class="form-group" v-if="numberPlayer>=6">
              <input type="text" v-model="playerSix" class="form-control" id="exampleInputEmail6" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <div class="form-group" v-if="numberPlayer>=8">
              <label for="exampleInputEmail1">Tim 4</label>
              <input type="text" v-model="playerSeven" class="form-control" id="exampleInputEmail7" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <div class="form-group" v-if="numberPlayer>=8">
              <input type="text" v-model="playerEight" class="form-control" id="exampleInputEmail8" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <div class="form-group" v-if="numberPlayer==10">
              <label for="exampleInputEmail1">Tim 5</label>
              <input type="text" v-model="playerNine" class="form-control" id="exampleInputEmail9" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <div class="form-group" v-if="numberPlayer==10">
              <input type="text" v-model="playerTen" class="form-control" id="exampleInputEmail10" aria-describedby="emailHelp" placeholder="Unesi ime igraca">
            </div>
            <button v-if="numberPlayer==4" @click.prevent="addTeamOne();addTeamTwo();redirect()" type="submit" class="btn btn-primary">Pokreni igru</button>
            <button v-if="numberPlayer==6" @click.prevent="addTeamOne();addTeamTwo();addTeamThree();redirect()" type="submit" class="btn btn-primary"><router-link to="/game">Pokreni igru</router-link></button>
            <button v-if="numberPlayer==8" @click.prevent="addTeamOne();addTeamTwo();addTeamThree();addTeamFour();redirect()" type="submit" class="btn btn-primary"><router-link to="/game">Pokreni igru</router-link></button>
            <button v-if="numberPlayer==10" @click.prevent="addTeamOne();addTeamTwo();addTeamThree();addTeamFour();addTeamFive();redirect()" type="submit" class="btn btn-primary"><router-link to="/game">Pokreni igru</router-link></button>
           
          </form>
          



          

         
        </div>
        <div class="col-sm">
          
        </div>
      </div>
    </div>


    
  </div>
</template>


<script>
import storage from '@/storage.js'
export default {
  name:'newGame',
  
 data(){
    
    /*let igrac = {
      ime:''
    } */
    return {
      playerOne:"",
      playerTwo:"",
      playerThree:"",
      playerFour:"",
      playerFive:"",
      playerSix:"",
      playerSeven:"",
      playerEight:"",
      playerNine:"",
      playerTen:"",
      numberPlayer:"",
      //igrac
    };
  },

  methods:{
    addTeamOne(){
     
      storage.teamOne.igraci.push(this.playerOne);
      storage.teamOne.igraci.push(this.playerTwo);
      storage.numberOfTeams=1;

    },
    addTeamTwo(){
      
      storage.teamTwo.igraci.push(this.playerThree);
      storage.teamTwo.igraci.push(this.playerFour);
      storage.numberOfTeams=2;
      
    },
     addTeamThree(){
 
      storage.teamThree.igraci.push(this.playerFive);
      storage.teamThree.igraci.push(this.playerSix);
      storage.numberOfTeams=3;

    },
     addTeamFour(){

      storage.teamFour.igraci.push(this.playerSeven);
      storage.teamFour.igraci.push(this.playerEight);
      storage.numberOfTeams=4;

      
    },
     addTeamFive(){
      //this.igrac.ime=this.playerNine; traba dodat u data() strukturu igraca sa atributom ime 
      storage.teamFive.igraci.push(this.playerNine);
      storage.teamFive.igraci.push(this.playerTen);
      storage.numberOfTeams=5;
      
    },
    redirect(){
      this.$router.push({ path: 'game' })
    }
    
  
  }

} 
</script>

<style>


</style>