<template>
    <div class="container">

      <div>
        <Title />
      </div>

      <form class="searchbar">
        <input v-model="taskUser" placeholder="Ajoute une tâche ici" />
        <button v-on:click="newTask">Ajouter</button>
      </form>

      <div id="list">
        <ul>
          <li v-for="task in tasks" :key="task.id">
            {{ task.title }}
          </li>
        </ul>
      </div>
    </div>
</template>


<script>
import Title from './components/Title.vue';
import axios from 'axios';

  export default {
    el: '#list',
    data: function() {
      return {
        tasks: [
        {id: 1, title: 'acheter du pain', completed: false },
        {id: 2, title: 'nourrir les cats', completed: true},
        {id: 3, title: 'faire le ménage', completed: false}
        ],
        taskUser: "",
      }
    },
    mounted () {
      axios.get('https://jsonplaceholder.typicode.com/todos')
      .then(res => {
        this.tasks = res.data; 
        })
    },
    methods: {
      newTask: function (e) {
        e.preventDefault();
        this.tasks.push({
        id: this.tasks.lenght+1,
        title: this.taskUser,
        completed: false
      });
      }
    },
    components: { Title }
  }

  

</script>

<style>
  body {
        background-color: papayawhip;
      }

  .container {
    border: solid grey 1px;
    margin-left: 200px;
    margin-right: 200px;
    height: 800px;
  }

  .searchbar {
    display:flex;
    justify-content: center;
    border-radius: 5px;
    
  }

  button {
    background-color: grey;
    color: white;
  }
</style>
