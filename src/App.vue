
<template>
  <input type="text" v-model="name.title">
</template>
<script setup>
import { ref, watch } from 'vue';

const name = ref({
  title: ''
})

watch(()=> name.value.title, (newValue, oldValue) => {
  document.title = newValue
})
</script>

<!-- CHAPITRE II -->
<!-- <template>
  <Layout>
    <template #header>
      <h1>Liste des taches a faire</h1>
    </template>
    <template v-slot:aside>
      A cote
    </template>
    <template v-slot:main>
      <button @click="showTimer = !showTimer">Aficher / Masquer</button>

      <Timer v-if="showTimer"></Timer>
    </template>
    <template #footer>
      Pied de page
    </template>
  </Layout>
  <form action="" @submit.prevent="addTodo">
    <fieldset role="group">
      <input 
        type="text"
        placeholder="Tâche a faire"
        v-model="newTodo">
      <button :disabled="newTodo.length === 0">Ajouter</button>
    </fieldset>
  </form>
  <div v-if="todos.length === 0">
    Vous n'avez pas des taches a faire :(
  </div>
  <div v-else>
    <ul>
      <li 
        v-for="todo in sortedTodos" 
        key="todo.date"
        :class="{completed: todo.completed}"
        >
        <!--<label>
          <input type="checkbox" v-model="todo.completed" id="">
          {{ todo.title }}
        </label>-->
        <!-- <Checkbox :label="todo.title" v-model="todo.completed"/>
      </li>
    </ul> 
    <label>
      <!--<input type="checkbox" v-model="hideCompleted">
      <Checkbox label="Masquer les taches terminees" v-model="hideCompleted"/>
    </label>
    <p v-if="remainingTodos > 0"> <span style="color: orangered; font-weight: bold">{{ remainingTodos }}</span> tache{{ remainingTodos > 1 ? 's' : '' }} a faire</p>
    <Button>
      Envoyer
    </Button>
  </div>
</template>-->

<!--<script setup>
import { computed, onMounted, ref } from 'vue';
import Checkbox from './Checkbox.vue';
import Button from './Button.vue';
import Layout from './Layout.vue';
import Timer from './Timer.vue';

const showTimer = ref(true);
const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([]);

onMounted(() => {
  fetch('https://jsonplaceholder.typicode.com/todos')
  .then(r => r.json())
  .then(v => todos.value = v .map(todo => ({ ...todo, date: todo.id})))
})
// const todos = ref([
//   {
//     title: 'Tache de test',
//     completed: true,
//     date: 1
//   },
//   {
//     title: 'Tache a faire',
//     completed: false,
//     date: 2
//   }
// ]);
const addTodo = () =>{
  todos.value.push({
    title: newTodo.value,
    completed: false,
    date: Date.now()
  })
  newTodo.value = ''
}
const sortedTodos = computed( () =>{
  const sortedTodos = todos.value.toSorted((a, b) => a.completed > b.completed ? 1 : -1)
  if (hideCompleted.value === true){
    return sortedTodos.filter(t => t.completed === false)
  }
  return sortedTodos;
})

const remainingTodos = computed (() =>{
  console.log("remaining");
  
  return todos.value.filter(t => t.completed === false).length
})

</script>
<style>
.completed{
  opacity: .5;
  text-decoration: line-through;
}
</style>

<!--COURS 1
<template>
  <h1>{{ greeting }}</h1>
  <div v-html="list"></div>
  <p :style="{color: count < 5 ? 'red' : 'green'}">Le compteur</p>
  <p :class="{active: count < 5}">Le compteur</p>
  <p class="second">{{ count }}</p>
  <div v-if="count==0">Incrementer pour commencer</div>
  <div v-else>
    <div v-if="count >= 5">Vous avez de depassee 10 fois</div>
    <div v-else>Vous avez de moins 5 fois</div>
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
      {{ book }} <button @click="deleteBook(book)">Supprimer</button>
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
</style> -->
