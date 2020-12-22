<template>
  <div class="about">


    <div class="container">
        <div class="row">
            <div class="col-sm">
            <table class="table">
              
              <tbody>
                <tr v-for="team in teams" :key="team.igraci[0]" >
                  <th scope="row">Team</th>
                  <td>{{team.igraci[0]}}</td>
                  <td>{{team.igraci[1]}}</td>
                  <td>{{team.bodovi}}</td>
                </tr>
              </tbody>
            </table>
            </div>
            <div class="col-sm">
            <router-link to="/newGame"><a class="btn btn-primary btn-lg" href="#" role="button">Nova igra?</a> </router-link>
            </div>
            <div class="col-sm">
            One of three columns
            </div>
        </div>
    </div>


    

  </div>
</template>

<script>
import storage from '@/storage.js';
export default {
  name:"highscore",
  data(){
    
    let teams=[];
    console.log(teams);

    return {
      teams
    }
  },
  
  mounted(){
    if(storage.numberOfTeams==2){
    this.teams.push(storage.teamOne);
    this.teams.push(storage.teamTwo);
    }
    else if(storage.numberOfTeams==3){
    this.teams.push(storage.teamOne);
    this.teams.push(storage.teamTwo);
    this.teams.push(storage.teamThree);
    }
    else if(storage.numberOfTeams==4){
    this.teams.push(storage.teamOne);
    this.teams.push(storage.teamTwo);
    this.teams.push(storage.teamThree);
    this.teams.push(storage.teamFour);
    }
    else if(storage.numberOfTeams==5){
    this.teams.push(storage.teamOne);
    this.teams.push(storage.teamTwo);
    this.teams.push(storage.teamThree);
    this.teams.push(storage.teamFour);
    this.teams.push(storage.teamFive);
    }

     this.teams.sort((a, b) => b.bodovi-a.bodovi)
  }


}
</script>