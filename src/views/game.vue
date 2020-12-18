<template>
  <div class="about">

    <div class="container">
        <div class="row">
            <div class="col-sm">
            
            </div>
            <div class="col-sm">
            
           
            {{randomWord.ime +" "+randomWord.bodovi}}

            <br>
            <a class="btn btn-primary btn-lg" href="#" role="button" style="background-color:green" @click.prevent="getWord()" onclick="style.display = 'none'">Zapocni</a>
            <br>
            <a class="btn btn-primary btn-lg" href="#" role="button" style="background-color:green" @click.prevent="getWord();correct()">tocno</a>
            <a class="btn btn-primary btn-lg" href="#" role="button" style="background-color:red"  @click.prevent="getWord();incorrect()">netocno</a>
            <br>
            <a class="btn btn-primary btn-lg" href="#" role="button" style="background-color:green" @click.prevent="printPlayer()">PRINTAJ</a>
            <router-link to="/highscore"><a class="btn btn-primary btn-lg" href="#" role="button">Pogledaj rezultate</a> </router-link>
            </div>
            <div class="col-sm">
            One of three columns
            </div>
        </div>
    </div>


      
  </div>
</template>

<script>
import storage from "@/storage.js"
export default {

  

  data(){

    
    let randomWord={
      ime:'',
      bodovi:''
    };

    return{
      randomWord,
      
    }
  },

  methods:{
    getWord(){
      let rijeci=[];
      rijeci=storage.rijeci;

      let rijec = rijeci[Math.floor(Math.random() * rijeci.length)];
      console.log("get word:" + rijec.ime+" "+rijec.bodovi);
      this.randomWord.ime=rijec.ime;
      this.randomWord.bodovi=rijec.bodovi;

    },
    correct(){
      console.log("Tocno");
    },
    incorrect(){
      console.log("Netocno");
    },
    printPlayer(){
      console.log("TIM1: "+storage.teamOne.igraci+" bodovi: "+storage.teamOne.bodovi);
      console.log("TIM2: "+storage.teamTwo.igraci+" bodovi: "+storage.teamTwo.bodovi);
      console.log("TIM3: "+storage.teamThree.igraci+" bodovi: "+storage.teamThree.bodovi);
      console.log("TIM4: "+storage.teamFour.igraci+" bodovi: "+storage.teamFour.bodovi);
      console.log("TIM5: "+storage.teamFive.igraci+" bodovi: "+storage.teamFive.bodovi);
    }

  },


  

}

</script>

