<template>
  <div>
    <div class="program-container">
      <div class="d-flex ai-center flex-wrap">
        <div class="program-container__title">
          <h2 class="text-uppercase">program</h2>
        </div>
        <div class="program-container__details">
          <span class="d-block">This conference run through all 4 days from 23 - 26 May 2016</span>
          <span class="d-block">We also provide free lunch and coffee break in each day</span>
        </div>
        <div class="program-container__link">
          <a href="#" class="text-capitalize">view full program</a>
        </div>
        <div class="program-container__program d-flex flex-wrap">
          <div class="program-days">
            <ul class="row">
              <li v-for="elm in program" :key="elm.id" class="col-2 programDays" @click="switchDay()">
                <h3 class="text-uppercase">{{elm.day}}</h3>
                <span>{{elm.date}}</span>
              </li>
              <li v-for="elm in slotVuoti" :key="elm.id" class="col-2">
                <h3 class="text-uppercase">{{elm.day}}</h3>
                <span>{{elm.date}}</span>
              </li>
            </ul>
          </div>
          <div class="program-details row bg-lightgray">
            <div class="program-details__left">
              <div class="d-flex ai-center flex-wrap">
                <span class="col-12"><i class="fa-solid fa-clock mr-2"></i>{{program[currentIndex].schedule}}</span>
                <span class="col-12 text-uppercase"><i class="fa-solid fa-location-arrow mr-2"></i>{{program[currentIndex].location}}</span>
                <span class="col-12 text-uppercase speaker-of-day"><i class="fa-solid fa-user mr-2"></i>{{program[currentIndex].speaker}}</span>
              </div>
            </div>
            <div class="program-details__right">
              <div class="ml-3">
                <h4 class="text-uppercase">{{program[currentIndex].title}}</h4>
                <span class="d-block">{{program[currentIndex].description}}</span>
                <img :src="program[currentIndex].speakerImg" :alt="program[currentIndex].speaker">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <LocationComp/>
  </div>
</template>

<script>
import LocationComp from "./LocationComp.vue";

export default {
name: 'ProgramComp',
components : {
  LocationComp
},
data(){
  return{
    program : [
      {
        day : "day 1",
        date : "23 May 2019",
        schedule : "09:00 - 10:30",
        location : "room a",
        speaker : "laurence francis",
        title : "welcoming and introduction",
        description : "Vestibulum ud ligula porta felis euismod semper. Nullarm quis risus eget urna mollis ornare vel eu leo. Donec ullamcorper nulla non metus auctor fringilla. Aenean lacinia bibendum nulla sed consectetur.",
        speakerImg : require("../../assets/img/speaker-8-150x150.jpg")
      },
      {
        day : "day 2",
        date : "24 May 2019",
        schedule : "09:00 - 10:30",
        location : "room a",
        speaker : "patrick spencer",
        title : "lorem ipsum",
        description : "Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis minus possimus recusandae est nihil velit voluptatem illo deserunt eligendi id qui eos dolore soluta repellendus quis, atque accusantium ipsum minima?",
        speakerImg : require("../../assets/img/speaker-6-150x150.jpg")
      },
      {
        day : "day 3",
        date : "25 May 2019",
        schedule : "09:00 - 10:30",
        location : "room a",
        speaker : "janet jones",
        title : "lorem ipsum",
        description : "Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis minus possimus recusandae est nihil velit voluptatem illo deserunt eligendi id qui eos dolore soluta repellendus quis, atque accusantium ipsum minima?",
        speakerImg : require("../../assets/img/speaker-5-150x150.jpg")
      },
      {
        day : "day 4",
        date : "26 May 2019",
        schedule : "09:00 - 10:30",
        location : "room a",
        speaker : "michael dover",
        title : "lorem ipsum",
        description : "Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis minus possimus recusandae est nihil velit voluptatem illo deserunt eligendi id qui eos dolore soluta repellendus quis, atque accusantium ipsum minima?",
        speakerImg : require("../../assets/img/speaker-4-150x150.jpg")
      },
    ],
    slotVuoti : [
      {
        day : "",
        date : "",
        schedule : "",
        location : "",
        speaker : "",
        title : "",
        description : "",
        speakerImg : ""
      },
      {
        day : "",
        date : "",
        schedule : "",
        location : "",
        speaker : "",
        title : "",
        description : "",
        speakerImg : ""
      },
    ],
    currentIndex : 0,
  }
},
methods : {
  switchDay(){
    if(this.currentIndex == 3){
      this.currentIndex = 0
    } else {
      this.currentIndex += 1;
    }
  }
}
}
</script>

<style scoped lang='scss'>
.program-container{
  width: 70%;
  margin: 4em auto 3em;
  &__title{
    flex-basis: 20%;
    letter-spacing: 0.2em;
  }
  &__details{
    flex-basis: 60%;
    font-size: 0.9rem;
    color: #868686;
  }
  &__link{
    flex-basis: 20%;
    text-align: right;
    a{
      color: #f72b0c;
      font-family: 'Libre Bodoni', serif;
      font-size: 0.9rem;
      }
  }
  &__program{
    margin: 3em 0;
    .program-days{
      flex-basis: 100%;
      li{
        background-color: #f72b0c;
        color: #fff;
        padding: 1em;
        border-right: 1px solid #bf351f;
        h3{font-size: 1rem;}
        span{font-size: 0.9rem;}
      }
      .programDays:hover{background-color: #bf351f;}
    }
  }
}

.program-details{
  padding: 2em 0;
  color: #868686;
  &__left{
    flex-basis: 30%;
    display: flex;
    margin-left: 3em;
    .speaker-of-day{color: #f72b0c;}
    .fa-solid{color: #868686;}
  }
  &__right{
    flex-basis: 70%;
    h4{
      font-size: 1.3rem;
      letter-spacing: 0.1em;
      margin-bottom: 1em;
    }
    span{
      font-size: 0.9rem;
    }
    img{
      margin-top: 1em;
      max-width: 100%;
      height: auto;
      width: 8%;
    }
  }
}
</style>