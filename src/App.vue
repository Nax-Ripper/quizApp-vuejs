
<script setup>
import q from './data/quizes.json'
import {ref, watch} from 'vue';

const quizzes = ref(q);
const search = ref('');

watch(search,()=>{
  console.log('hi');
  quizzes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})


</script>


<template>
  <div class="container">
    
    <header>
      <h1> Quizzes</h1>
      <input  type="text" placeholder="Find..." v-model.trim="search">
    </header>

      <div class="options-container">
        <div class="card" v-for="quiz in quizzes" :key="quiz.id">
          <img :src=quiz.img alt="">
          <div class="card-text" >
            <h2>{{quiz.name}}</h2>
            <p>{{ quiz.questions.length }} Questions</p>
          </div>

        </div>

      </div>

  </div>
</template>

<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
}

header{
  margin-bottom:10px;
  margin-top: 30px;
  display: flex;
  align-items: center;
  
}

header h1{
  font-weight: bold;
  margin-right: 30px;
  margin-bottom: 35px;
  

 

}

header input{
  border: none;
  background-color:rgba(128,128,128,0.1);
  padding: 15px;
  border-radius:10px;
}

.options-container{
  display: flex;
  flex-wrap: wrap;
  margin-top:40px;
}


/*CARD */

.card{
  width: 300px;
  border-radius: 5%;
  cursor: pointer;
  overflow: hidden;
  box-shadow: 5px 5px 10px rgba(0,0,0,0.1);
  margin-right:20px ;
  margin-bottom:20px ;
  
  
 
}
.card img{
  width: 100%;
  height: 190px;
  margin: 0;

}

.card .card-text{
  padding: 0 5px;
}

.card .card-text h2{
  font-weight: bold;

}
</style>