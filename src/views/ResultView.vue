<template>
  <div class="about">
    <h1>This is the result view!</h1>
    
    <div>
      <h3>Vilket ramverk har du använt dig av?</h3>
      <PieChart :result="pieOne()"/>
    </div>
  
    <div>
      <h3>Hur många års erfarenhet av programmering har du?</h3>
      <PieChart :result="pieTwo()"/>
    </div>
    <div>
      <h3>Hur mycket erfarenhet av html, css och javascript hade du innan du började med ramverket?</h3>
      <barChart class="barSize" :result="barOne()"/> 
    </div>
    <div>
      <h3>Hur lätt var det att lära dig ramverket?</h3>
      <barChart class="barSize" :result="barTwo()"/> 
    </div>
    <div>
      <h3>Hur effektivt tycker du att ramverket är?</h3>
      <barChart class="barSize" :result="barThree()"/> 
    </div>
    <div>
      <h3>Hur mycket underlättar ramverket ditt programmerande?</h3>
      <barChart class="barSize" :result="barFour()"/> 
    </div>
    <div>
    <div class="d-flex">
      <h5 >Är det lätt att minnas <br>  ramverkets syntax och dess uppbyggnad? </h5>
      <h5 style="margin-left: 6rem;">Om du har haft en paus från ramverket,<br> tycker du det var lätt att minnas<br>  hur det fungerade när du kom tillbaka? </h5>
    </div>
    <div class="d-flex">
      <barChart  :result="barFive()"/> <barChart :result="barSix()"/> </div>
  </div>
  <div>
  <div class="d-flex">
      <h5 >Tycker du att ramverket krånglar?</h5>
      <h5 style="margin-left: 10rem;" >Om det krånglar, är det lätt att lösa problemen?</h5>
    </div>
    <div class="d-flex">
      <barChart :result="barSeven()"/> <barChart :result="barEight()"/> </div>
  </div>
    <div>
      <h3>Tycker du om ramverket?</h3>
      <barChart class="barSize" :result="barNine()"/> 
    </div>
    <div>
      <h3 >Om du har använt dig av både React och Vue, vilket föredrar du?</h3>
      <PieChart :result="pieThree()"/>
    </div>
  

  
  </div>
</template>

<script>
import PieChart from '../components/Pie.vue'
import barChart from '../components/BarChart.vue'
import SurveyData from '../Data/SurveyData.json';
export default {
  name: 'ResultView',
  components: {
    PieChart,
    barChart
  },
  data() {
    return {
     vue: "Vue",
     react:"React",
     other:"Annat"
    
    }
  },
  methods: {
    pieOne() {
            const totalSurveys = SurveyData.length;
            let vueAnswer = 0;
            let reactAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd["Vilket ramverk har du använt dig av?"])

            vueAnswer = answersForQuestion.filter(a => a == "Vue.js").length
            reactAnswer = answersForQuestion.filter(a => a == "React").length


            const resultData = [];

            resultData['Vue'] = ((vueAnswer / totalSurveys) * 100);
            resultData['React'] = ((reactAnswer / totalSurveys) * 100);

            /*
            [Vue]: 50
            [React]: 50
            */
            return resultData;
        },
        pieTwo() {
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd["Hur många års erfarenhet av programmering har du?"])

            firstAnswer = answersForQuestion.filter(a => a == "0-1").length
            secondAnswer = answersForQuestion.filter(a => a == "2-3").length
            thirdAnswer = answersForQuestion.filter(a => a == "4+").length

            const resultData = [];

            resultData["0-1"] = ((firstAnswer / totalSurveys) * 100);
            resultData['2-3'] = ((secondAnswer / totalSurveys) * 100);
            resultData['4+'] = ((thirdAnswer / totalSurveys) * 100);

            return resultData;
        },
        pieThree() {
    
          const totalSurveys = SurveyData.length;
            let vueAnswer = 0;
            let reactAnswer = 0;
            let otherAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd["Om du har använt dig av både React och Vue, vilket föredrar du?"])

            vueAnswer = answersForQuestion.filter(a => a == "Vue").length
            reactAnswer = answersForQuestion.filter(a => a == "React").length
            otherAnswer = answersForQuestion.filter(a => a == "Inget").length

            const resultData = [];

            resultData['Vue'] = ((vueAnswer / totalSurveys) * 100);
            resultData['React'] = ((reactAnswer / totalSurveys) * 100);
            resultData['Inget'] = ((otherAnswer / totalSurveys) * 100);

            return resultData;
        },
        barOne(){
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;
            let fourthAnswer = 0;
            let fifthAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd[ "Hur mycket erfarenhet av html, css och javascript hade du innan du började med ramverket?"])

            firstAnswer = answersForQuestion.filter(a => a == 1).length
            secondAnswer = answersForQuestion.filter(a => a == 2).length
            thirdAnswer = answersForQuestion.filter(a => a == 3).length
            fourthAnswer = answersForQuestion.filter(a => a == 4).length
            fifthAnswer = answersForQuestion.filter(a => a == 5).length

            const resultData = [];

            resultData[1] = ((firstAnswer / totalSurveys) * 100);
            resultData[2] = ((secondAnswer / totalSurveys) * 100);
            resultData[3] = ((thirdAnswer / totalSurveys) * 100);
            resultData[4] = ((fourthAnswer / totalSurveys) * 100);
            resultData[5] = ((fifthAnswer / totalSurveys) * 100);

            return resultData;
        },
        barTwo(){
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;
            let fourthAnswer = 0;
            let fifthAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd[ "Hur lätt var det att lära dig ramverket?"])

            firstAnswer = answersForQuestion.filter(a => a == 1).length
            secondAnswer = answersForQuestion.filter(a => a == 2).length
            thirdAnswer = answersForQuestion.filter(a => a == 3).length
            fourthAnswer = answersForQuestion.filter(a => a == 4).length
            fifthAnswer = answersForQuestion.filter(a => a == 5).length

            const resultData = [];

            resultData[1] = ((firstAnswer / totalSurveys) * 100);
            resultData[2] = ((secondAnswer / totalSurveys) * 100);
            resultData[3] = ((thirdAnswer / totalSurveys) * 100);
            resultData[4] = ((fourthAnswer / totalSurveys) * 100);
            resultData[5] = ((fifthAnswer / totalSurveys) * 100);

            return resultData;
        },
        barThree(){
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;
            let fourthAnswer = 0;
            let fifthAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd[ "Hur effektivt tycker du att ramverket är?"])

            firstAnswer = answersForQuestion.filter(a => a == 1).length
            secondAnswer = answersForQuestion.filter(a => a == 2).length
            thirdAnswer = answersForQuestion.filter(a => a == 3).length
            fourthAnswer = answersForQuestion.filter(a => a == 4).length
            fifthAnswer = answersForQuestion.filter(a => a == 5).length

            const resultData = [];

            resultData[1] = ((firstAnswer / totalSurveys) * 100);
            resultData[2] = ((secondAnswer / totalSurveys) * 100);
            resultData[3] = ((thirdAnswer / totalSurveys) * 100);
            resultData[4] = ((fourthAnswer / totalSurveys) * 100);
            resultData[5] = ((fifthAnswer / totalSurveys) * 100);

            return resultData;
        },
        barFour(){
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;
            let fourthAnswer = 0;
            let fifthAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd[ "Hur mycket underlättar ramverket ditt programmerande?"])

            firstAnswer = answersForQuestion.filter(a => a == 1).length
            secondAnswer = answersForQuestion.filter(a => a == 2).length
            thirdAnswer = answersForQuestion.filter(a => a == 3).length
            fourthAnswer = answersForQuestion.filter(a => a == 4).length
            fifthAnswer = answersForQuestion.filter(a => a == 5).length

            const resultData = [];

            resultData[1] = ((firstAnswer / totalSurveys) * 100);
            resultData[2] = ((secondAnswer / totalSurveys) * 100);
            resultData[3] = ((thirdAnswer / totalSurveys) * 100);
            resultData[4] = ((fourthAnswer / totalSurveys) * 100);
            resultData[5] = ((fifthAnswer / totalSurveys) * 100);

            return resultData;
        },
        barFive(){
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;
            let fourthAnswer = 0;
            let fifthAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd[   "Är det lätt att minnas ramverkets syntax och dess uppbyggnad?"])

            firstAnswer = answersForQuestion.filter(a => a == 1).length
            secondAnswer = answersForQuestion.filter(a => a == 2).length
            thirdAnswer = answersForQuestion.filter(a => a == 3).length
            fourthAnswer = answersForQuestion.filter(a => a == 4).length
            fifthAnswer = answersForQuestion.filter(a => a == 5).length

            const resultData = [];

            resultData[1] = ((firstAnswer / totalSurveys) * 100);
            resultData[2] = ((secondAnswer / totalSurveys) * 100);
            resultData[3] = ((thirdAnswer / totalSurveys) * 100);
            resultData[4] = ((fourthAnswer / totalSurveys) * 100);
            resultData[5] = ((fifthAnswer / totalSurveys) * 100);

            return resultData;
        },
        barSix(){
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;
            let fourthAnswer = 0;
            let fifthAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd["Om du har haft en paus från ramverket, tycker du det var lätt att minnas hur det fungerade när du kom tillbaka?"])

            firstAnswer = answersForQuestion.filter(a => a == 1).length
            secondAnswer = answersForQuestion.filter(a => a == 2).length
            thirdAnswer = answersForQuestion.filter(a => a == 3).length
            fourthAnswer = answersForQuestion.filter(a => a == 4).length
            fifthAnswer = answersForQuestion.filter(a => a == 5).length

            const resultData = [];

            resultData[1] = ((firstAnswer / totalSurveys) * 100);
            resultData[2] = ((secondAnswer / totalSurveys) * 100);
            resultData[3] = ((thirdAnswer / totalSurveys) * 100);
            resultData[4] = ((fourthAnswer / totalSurveys) * 100);
            resultData[5] = ((fifthAnswer / totalSurveys) * 100);

            return resultData;
        },
        barSeven(){
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;
            let fourthAnswer = 0;
            let fifthAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd[ "Tycker du att ramverket krånglar?"])

            firstAnswer = answersForQuestion.filter(a => a == 1).length
            secondAnswer = answersForQuestion.filter(a => a == 2).length
            thirdAnswer = answersForQuestion.filter(a => a == 3).length
            fourthAnswer = answersForQuestion.filter(a => a == 4).length
            fifthAnswer = answersForQuestion.filter(a => a == 5).length

            const resultData = [];

            resultData[1] = ((firstAnswer / totalSurveys) * 100);
            resultData[2] = ((secondAnswer / totalSurveys) * 100);
            resultData[3] = ((thirdAnswer / totalSurveys) * 100);
            resultData[4] = ((fourthAnswer / totalSurveys) * 100);
            resultData[5] = ((fifthAnswer / totalSurveys) * 100);

            return resultData;
        },
        barEight(){
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;
            let fourthAnswer = 0;
            let fifthAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd[ "Om det krånglar, är det lätt att lösa problemen?"])

            firstAnswer = answersForQuestion.filter(a => a == 1).length
            secondAnswer = answersForQuestion.filter(a => a == 2).length
            thirdAnswer = answersForQuestion.filter(a => a == 3).length
            fourthAnswer = answersForQuestion.filter(a => a == 4).length
            fifthAnswer = answersForQuestion.filter(a => a == 5).length

            const resultData = [];

            resultData[1] = ((firstAnswer / totalSurveys) * 100);
            resultData[2] = ((secondAnswer / totalSurveys) * 100);
            resultData[3] = ((thirdAnswer / totalSurveys) * 100);
            resultData[4] = ((fourthAnswer / totalSurveys) * 100);
            resultData[5] = ((fifthAnswer / totalSurveys) * 100);

            return resultData;
        },
        barNine(){
          const totalSurveys = SurveyData.length;
            let firstAnswer = 0;
            let secondAnswer = 0;
            let thirdAnswer = 0;
            let fourthAnswer = 0;
            let fifthAnswer = 0;

            const answersForQuestion = SurveyData.map(sd => sd[  "Tycker du om ramverket?"])

            firstAnswer = answersForQuestion.filter(a => a == 1).length
            secondAnswer = answersForQuestion.filter(a => a == 2).length
            thirdAnswer = answersForQuestion.filter(a => a == 3).length
            fourthAnswer = answersForQuestion.filter(a => a == 4).length
            fifthAnswer = answersForQuestion.filter(a => a == 5).length

            const resultData = [];

            resultData[1] = ((firstAnswer / totalSurveys) * 100);
            resultData[2] = ((secondAnswer / totalSurveys) * 100);
            resultData[3] = ((thirdAnswer / totalSurveys) * 100);
            resultData[4] = ((fourthAnswer / totalSurveys) * 100);
            resultData[5] = ((fifthAnswer / totalSurveys) * 100);

            return resultData;
        }
  },
}
</script>
