<template>
  <div class="home">
    <AppBar title="TODO" left="bars" right="search" />
    <Avatar :name="name" :imgSrc="imgSrc" />
    <Gradient />
    <TodoList />
    <TodoDetail />
    <TodoEditing/>
    <FloatingButton />
  </div>
</template>

<script>
import AppBar from '../components/AppBar.vue'
import Avatar from '../components/Avatar.vue'
import Gradient from '../components/Gradient.vue'
import TodoList from '../components/TodoList.vue'
import TodoDetail from '../components/TodoDetail.vue'
import TodoEditing from '../components/TodoEditing.vue'
import FloatingButton from '../components/FloatingButton.vue'
export default {
  components: {
    AppBar,
    Avatar,
    Gradient,
    TodoList,
    TodoDetail,
    TodoEditing,
    FloatingButton
  },
  props: {
    name: {
      type: String,
      required: true
    },
    imgSrc: {
      type: String,
      required: true
    }
  }
}
</script>

<style>
.home {
  height: 100%;
  width: 100%;
  overflow: hidden;
  color: white;
}
</style>
