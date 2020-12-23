<template>
  <div class="about">

    <div class="container">
        <div class="row">
            <div class="col-sm">
              
            </div>
            <div class="col-sm">
            
            <div v-show="cTeam.igraci[0]!=null">
              {{cTeam.igraci[0]+" "+cTeam.igraci[1]+ " bodovi: "+cTeam.bodovi }}
            </div>

            <br><br><br>
           
            RIJEC: {{randomWord.ime }}
            <br>
            BODOVI: {{randomWord.bodovi}}

            <br>
            <a class="btn btn-primary btn-lg" href="#" role="button" style="background-color:green" @click.prevent=";getTeam(counter);getWord()" onclick="style.display = 'none'">Zapocni</a>
            <br>
            <a class="btn btn-primary btn-lg" href="#" role="button" style="background-color:green" @click.prevent="correct();getWord()">tocno</a>
            <a class="btn btn-primary btn-lg" href="#" role="button" style="background-color:red"  @click.prevent="incorrect();getWord()">netocno</a>
            <br>
            </div>
            <div class="col-sm">
           
            </div>
        </div>
    </div>


      
  </div>
</template>

<script>
import storage from "@/storage.js"
export default {
  name:"game",
  

  data(){
    let counter=1; //counter za timove (koji tim je na redu)
    let wordCounter=1; //counter za rijeci u teamu
    let roundCounter=1; //counter za runde


    
    //current Team na redu getTeam(),switchTeam()
    let cTeam={
      igraci:[],
      bodovi:0
    }

    //genirana random rijec getWord()
    let randomWord={
      ime:'',
      bodovi:''
    };

    return{
      randomWord,
      cTeam,
      counter,
      wordCounter,
      roundCounter
    }
  },

  methods:{
    getWord(){
      
      //ucitavanje random rijeci
      let rijeci=[];
      rijeci=storage.rijeci;
      let rijec = rijeci[Math.floor(Math.random() * rijeci.length)];
      console.log("get word:" + rijec.ime+" "+rijec.bodovi);
      console.log("word counter:"+this.wordCounter)
      this.randomWord.ime=rijec.ime;
      this.randomWord.bodovi=rijec.bodovi;

      //cekira dal je proslo 5 rijeci
      this.checkAndUpdate();
      
      //uvecavanje broja ispisanih rijeci u rundi za 1 (max 5 rijeci)
      this.wordCounter=this.wordCounter+1;

     

    },
    correct(){
      this.cTeam.bodovi=this.cTeam.bodovi+this.randomWord.bodovi;
    },
    incorrect(){
      this.cTeam.bodovi=this.cTeam.bodovi-(this.randomWord.bodovi/2);
    },

    checkAndUpdate(){
      //cekiranje dal je proslo 5 rijeci
      if(this.wordCounter>5){
        alert("osvojeno bodova:" + this.cTeam.bodovi );
      
        
        //ako je proslo 5 rijeci spremi trenutne bodove na bazu ovisno o timu
        if(this.counter==1){
          storage.teamOne.bodovi=storage.teamOne.bodovi+this.cTeam.bodovi;
        }
        if(this.counter==2){
          storage.teamTwo.bodovi=storage.teamTwo.bodovi+this.cTeam.bodovi;
        }
        if(this.counter==3){
          storage.teamThree.bodovi=storage.teamThree.bodovi+this.cTeam.bodovi;
        }
        if(this.counter==4){
          storage.teamFour.bodovi=storage.teamFour.bodovi+this.cTeam.bodovi;
        }
        if(this.counter==5){
          storage.teamFive.bodovi=storage.teamFive.bodovi+this.cTeam.bodovi;
        }

        //javi da se mjenjaju timovi
        alert("novi tim na redu!" );
        this.switchTeam();
        this.getTeam(this.counter);
      }
    },


    getTeam(brojac){
      
      
      
      //provjerava broj timova da vidi kolko timova mora vrtit (min 2-5)
      if(storage.numberOfTeams==2){
        if(brojac>2){
          this.counter=1;
          brojac=1;
          this.roundCounter=this.roundCounter+1; //uvecaj rundu za 1 kad izvrtis sve timove (u ovom slucaju 2 tima)
        }  
      }

      if(storage.numberOfTeams==3){
        if(brojac>3){
          this.counter=1;
          brojac=1;
          this.roundCounter=this.roundCounter+1;
        }
      }

      if(storage.numberOfTeams==4){
        if(brojac>4){
          this.counter=1;
          brojac=1;
          this.roundCounter=this.roundCounter+1;
        }
      }

      if(storage.numberOfTeams==5){
        if(brojac>5){
          this.counter=1;
          brojac=1;
          this.roundCounter=this.roundCounter+1;
        }
      }

      //kad dodje do odredjene runde zavrsava igru i prebacuje na highscore
      if(this.roundCounter==3){
            this.$router.push({ path: 'highscore' })
      }


      //ubacivanje odredjenog tima ovisno o trenutnom counteru (1-5) - koji je tim na redu
      if(brojac==1){
        this.cTeam.igraci=storage.teamOne.igraci;
        this.cTeam.bodovi=0;
        //console.log("tim1 na redu");
      }
      if(brojac==2){
        this.cTeam.igraci=storage.teamTwo.igraci;
        this.cTeam.bodovi=0;
      }
      if(brojac==3){
        this.cTeam.igraci=storage.teamThree.igraci;
        this.cTeam.bodovi=0;
      }
      if(brojac==4){
        this.cTeam.igraci=storage.teamFour.igraci;
        this.cTeam.bodovi=0;
      }
      if(brojac==5){
        this.cTeam.igraci=storage.teamFive.igraci;
        this.cTeam.bodovi=0;
      }
      
      
    },
    switchTeam(){
      //kad promjeni tim postavlja broj rijeci na 1 tako da se svaki put izvrti rijeci
      this.wordCounter=1;
      //uvecava counter timova za 1,ovisno koliko timova ima
      this.counter=this.counter+1;
    }

  },


  

}

</script>

