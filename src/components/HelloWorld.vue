<template>
  <v-container>
    <v-layout
      text-xs-center
      wrap
      justify-space-arount
    >
      <v-flex xs12>
        <v-text-field  v-model="description" @keydown.enter="addTodo"/>
      </v-flex>
        <v-flex xs3 :key="i" v-for="(todo, i) in todos" ml-3 mb-3>
          <v-card color=secundary>
            <div>
              {{todo}}
            </div>
            <v-btn @click="remove(i)" color=primary>
              x
            </v-btn>
          </v-card>
        </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
      todos: [],
      description: ""
    }),
    methods: {
      remove(index) {
        this.todos.splice(index, 1)
      },
      addTodo() {
        this.todos.push(this.description)
        this.description = ""
      }
    }
  }
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: all 800ms;
  transform: scale(1) rotateY(0deg);
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: scale(0.1) rotateY(-360deg);
  margin-left: -300px;   
}
</style>
