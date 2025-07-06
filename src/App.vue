<template>
  <h1>{{ greeting }}</h1>
  <div v-html="list"></div>
  <p :style="{color: count < 5 ? 'red' : 'green'}">Le compteur</p>
  <p :class="{active: count < 5}">Le compteur</p>
  <p class="second">{{ count }}</p>
  <div v-if="count==0">Incrementer pour commencer</div>
  <div v-else>
    <div v-if="count >= 5">Vous avez de depassee 10 fois</div>
    <div v-else>Vous avez de moins 10 fois</div>
  </div>
  <div class="btns">
    <button v-on:click="increment">Incrémenter</button>
    <button @click="decrement">Decrementer</button>
  </div>

  <class class="btns">
    <button @click="organiser()">A > Z</button>
    <button @click="reorganiser()">Z > A</button>
  </class>
  <ul>
    <li v-for="book in livresesoteriques">
      {{ book }} <button @click="deleteBook(book)">Supprime</button>
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue';
const name = 'APDLC ASBL';
const greeting = `Bienvenue à "${name}"!`
const count = ref(0);
console.log(`Compteur initialisé à ${count.value}`);
console.log(count);
const list = '<ul><li>Ardoise</li><li>Bille</li></ul>'

const livresesoteriques = ref([
  'La kabbale sacre',
  'Mystere d\'Eleseus',
  'Les plantes magiques',
  'Rituel de magie trantrique'
])

const increment = () => {
  count.value++;
};
const decrement = () => {
  if (count.value > 0) {
    count.value--;
  }
};
// setInterval(() => {
//   count.value++
// }, 1000);
const deleteBook = (book) => {
  livresesoteriques.value = livresesoteriques.value.filter(m => m != book)
}
const organiser = () => {
  livresesoteriques.value.sort((a,b) => a > b ? 1 : -1)
}
const reorganiser = () => {
  livresesoteriques.value.sort((a,b) => a > b ? -1 : 1)
}
</script>

<style>
h1{
  color: orangered;
}
.btns{
  display: flex;
  gap: 10px;
}
.second{
  color: rgb(136, 14, 184);
  font-size: 2em;
  font-weight: bold;
}
.active{
  display: none;
}
button{
  background-color: orangered;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 1em;
  cursor: pointer;
  border-radius: 5px;
  margin-bottom: 4px;
}
button:hover{
  background-color: darkorange;
}
</style>
