<template>
  <div class="hello">
    <h1 class="w3-animate-right">{{ msg }}</h1>
    <div class="button_container w3-animate-left ">
      <button class="start_button" @click="reset()">{{clik}}</button>
    </div>

    <div class="main_container_quiz w3-animate-top" v-if="start" >
      <h2>Zaczynamy, przed Tobą 5 pytań:</h2>
      <ul class="questions">
        <h2 class="title_1">Słynny dowódca 2 korpusu Polskich Sił Zbrojnych w czasie bitwy pod Monte Cassino to:</h2>
        <li class="answers">
<!--          <button class="button" v-bind:style="{ color:white, background: back }" @click="back='#2c3e50', white='white'">Władysław Anders</button>-->
<!--          <button class="button" v-bind:style="{ color:white, background: back }" @click="back='#2c3e50', white='white'">Henryk Sucharski</button>-->
<!--          <button class="button" v-bind:style="{ color:white, background: back }" @click="back='#2c3e50', white='white'">Stefan Orzechowski</button>-->

          <button :class="button011" @click="button011='button_choose', button012='button', button013='button', choosed1=1">Władysław Anders</button>
          <button :class="button012" @click="button011='button', button012='button_choose', button013='button', choosed1=2">Henryk Sucharski</button>
          <button :class="button013" @click="button011='button', button012='button', button013='button_choose', choosed1=3">Stefan Orzechowski</button>
        </li>

        <h2 class="title_1">Generał Józef Bem żył w latach 1794-1850. Przez historyków zwany jest bohaterem narodowym Polski i: </h2>
        <li class="answers">
          <button :class="button021" @click="button021='button_choose', button022='button', button023='button', choosed2=1">Stanów Zjednoczonych</button>
          <button :class="button022" @click="button021='button', button022='button_choose', button023='button', choosed2=2">Francji</button>
          <button :class="button023" @click="button021='button', button022='button', button023='button_choose', choosed2=3">Węgier</button>
        </li>

        <h2 class="title_1">Polski Hetman który zasłynął podczas walk ze szwedami w XVII. <br>
          Jego nazwisko jest obecnie w w tekscie "Mazurka Dąbrowskiego". Mowa o: </h2>
        <li class="answers">
          <button :class="button031" @click="button031='button_choose', button032='button', button033='button', choosed3=1">Józefie Wybickim</button>
          <button :class="button032" @click="button031='button', button032='button_choose', button033='button', choosed3=2">Stefanie Czarnicekim</button>
          <button :class="button033" @click="button031='button', button032='button', button033='button_choose', choosed3=3">Tadeuszu Kościuszce</button>
        </li>

        <h2 class="title_1">Jak nazywała się formacja wojskowa zorganizowana 1797 roku we Włoszech przez Jana Henryka Dąbrowskiego? </h2>
        <li class="answers">
          <button :class="button041" @click="button041='button_choose', button042='button', button043='button', choosed4=1">Armia Krajowa</button>
          <button :class="button042" @click="button041='button', button042='button_choose', button043='button', choosed4=2">Legiony Polskie</button>
          <button :class="button043" @click="button041='button', button042='button', button043='button_choose', choosed4=3">Pierwsza Dywizja Narodowych Sił Zbrojnych Księstwa Warzszawskiego</button>
        </li>
        <h2 class="title_1">Od nazwiska tego wybitnego dowódcy pochodzi nazwa najwyższego szczytu w Australii. Chodzi o: </h2>
        <li class="answers">
          <button :class="button051" @click="button051='button_choose', button052='button', button053='button', choosed5=1">Józefa Piłsudskiego</button>
          <button :class="button052" @click="button051='button', button052='button_choose', button053='button', choosed5=2">Józefa Poniatowskiego</button>
          <button :class="button053" @click="button051='button', button052='button', button053='button_choose', choosed5=3">Tadeusza Kościuszko</button>
        </li>
      </ul>
      <button class="start_button"  @click="stop=true, start=false, again=true, sprawdzanie()">Sprawdź Wyniki!</button>
    </div>
    <h1 v-if="stop || again">Twój wynik to: {{wynik}}/5</h1>
    <h1 v-if="(stop || again) && wynik==5">GRATULACJE!</h1>
    <button v-if="stop" class="start_button"  @click="start=true, again=false, odpowiedzi() ">Pokaż Odpowiedzi</button>
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data(){
    return{
      start:false,
      stop:false,
      again:false,
      clik:"Kliknij aby zacząć quiz!",
      choosed1:0,
      choosed2:0,
      choosed3:0,
      choosed4:0,
      choosed5:0,
      wynik:0,
      button011:'button',
      button012:'button',
      button013:'button',
      button021:'button',
      button022:'button',
      button023:'button',
      button031:'button',
      button032:'button',
      button033:'button',
      button041:'button',
      button042:'button',
      button043:'button',
      button051:'button',
      button052:'button',
      button053:'button'
    }
  },
  methods:
      {
        reset(){
          this.button011='button'
          this.button012='button'
          this.button013='button'
          this.button021='button'
          this.button022='button'
          this.button023='button'
          this.button031='button'
          this.button032='button'
          this.button033='button'
          this.button041='button'
          this.button042='button'
          this.button043='button'
          this.button051='button'
          this.button052='button'
          this.button053='button'
          this.stop=false
          this.again=false
          this.start=true;
          this.clik="Zacznij od początku"
        },
        sprawdzanie(){
          this.wynik=0;
          if((this.button011=='button_choose')||(this.button011=='correct_button') )
          {
            this.wynik++;
            this.button011='correct_button'
          }
          if((this.button023=='button_choose')||(this.button023=='correct_button') )
          {
            this.wynik++;
            this.button023='correct_button'
          }
          if((this.button032=='button_choose')||(this.button032=='correct_button') )
          {
            this.wynik++;
            this.button032='correct_button'
          }
          if((this.button042=='button_choose')||(this.button042=='correct_button') )
          {
            this.wynik++;
            this.button042='correct_button'
          }
          if((this.button053=='button_choose')||(this.button053=='correct_button') )
          {
            this.wynik++;
            this.button053='correct_button'
          }
        },
        odpowiedzi() {
          if((this.button011!='button_choose')&&(this.button011!='correct_button') ) {
             this.button011='good_button'
              if(this.choosed1==2)
              {
                this.button012="bad_button"
              }
              if(this.choosed1==3)
              {
                this.button013="bad_button"
              }
          }
          if((this.button023!='button_choose')&&(this.button023!='correct_button') ) {
          this.button023='good_button'
            if(this.choosed2==1)
              {
                this.button021="bad_button"
              }
              if(this.choosed2==2)
              {
                this.button022="bad_button"
              }
          }
          if((this.button032!='button_choose')&&(this.button032!='correct_button') ) {
          this.button032='good_button'
            if(this.choosed3==1)
              {
                this.button031="bad_button"
              }
              if(this.choosed3==3)
              {
                this.button033="bad_button"
              }
          }
          if((this.button042!='button_choose')&&(this.button042!='correct_button') ) {
            this.button042 = 'good_button'
            if(this.choosed4==1)
              {
                this.button041="bad_button"
              }
              if(this.choosed4==3)
              {
                this.button043="bad_button"
              }
          }
          if((this.button053!='button_choose')&&(this.button053!='correct_button') ) {
            this.button053 = 'good_button'
            if(this.choosed5==1)
              {
                this.button051="bad_button"
              }
              if(this.choosed5==2)
              {
                this.button052="bad_button"
              }
          }
        }
      }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


.activeClass
{
  color: #e0c708;
}
.errorClass
{
  background-color: #2c3e50;
}

h1
{
  font-size: 50px;
  text-shadow: 0 0 0.2em #2c3e50 , 0 0 0.2em #e0c708, 0 0 0.2em #2c3e50;
}
h2
{
  text-shadow: 0 0 0.2em #2c3e50, 0 0 0.2em #e0c708, 0 0 0.2em #2c3e50;
}
.button_container
{
  margin: 20px;
}
.start_button
{
  height: 50px;
  min-width: 300px;
  background: linear-gradient(to left, grey, black);
  border-radius: 20px;
  color: white;
  font-size: 20px;
  transition: 1s;
  border-color: grey;
}

.start_button:hover
{
  animation: blink 2s linear infinite;
  background: linear-gradient(to left, black, grey);
  cursor: pointer;
}

@keyframes blink {
  25%
  {
    transform: scale(1.02);
  }
  50%
  {
    transform: scale(1);
  }
  75%
  {
    transform: scale(0.98);
  }
}

.main_container_quiz
{
    margin: 50px 0 50px 0;
}
.questions
{
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-left: 10vw;
}
.title_1
{
   text-shadow: 0 0 0.2em grey, 0 0 0.2em #e0c708, 0 0 0.2em grey;
}
.answers
{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.button
{
  height: 50px;
  width: 60vw ;
  background:white;
  border-radius: 3px;
  color: #2c3e50;
  font-size: 20px;
  transition: 0.5s;
  margin: 5px;
  text-align: left;
}
.button:hover
{
  cursor: pointer;
  background: linear-gradient(to left, grey, white);
}
.button_choose:hover
{
  cursor: pointer;
  background: linear-gradient(to left, grey, grey);
  color: #2c3e50;
}
.correct_button:hover
{
  cursor: pointer;
  background: linear-gradient(to left, grey, white);
  color: #2c3e50;
}
.good_button:hover
{
  cursor: pointer;
  background: linear-gradient(to left, grey, white);
  color: #2c3e50;
}

.button_choose
{
  height: 50px;
  width: 60vw ;
  background: #2c3e50;
  border-radius: 3px;
  color: white;
  font-size: 20px;
  transition: 1s;
  margin: 5px;
  text-align: left;
}
.correct_button
{
  height: 50px;
  width: 60vw ;
  background: green;
  border-radius: 3px;
  color: white;
  font-size: 20px;
  transition: 1s;
  margin: 5px;
  text-align: left;
}
.good_button
{
  height: 50px;
  width: 60vw ;
  background: linear-gradient(to left, darkgreen, white);
  border-radius: 3px;
  color: #2c3e50;
  font-size: 20px;
  transition: 1s;
  margin: 5px;
  text-align: left;
}

.bad_button
{
  height: 50px;
  width: 60vw ;
  background: darkred;
  border-radius: 3px;
  color: white;
  font-size: 20px;
  transition: 1s;
  margin: 5px;
  text-align: left;
}



</style>
