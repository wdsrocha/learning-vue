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
      <transition-group name="fade">
      <!-- Jeová me dê forças -->
          <v-card
            xs12
            color=secundary
            :key="i"
            v-for="(todo, i) in todos"
            ml-3
            mb-3
          >
            <div>
              {{todo}}
            </div>
            <v-btn @click="remove(i)" color=primary>
              x
            </v-btn>
          </v-card>
      </transition-group>
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
  transition: all 400ms;
  transform: scale(1)
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: scale(0.1)
}
</style>
