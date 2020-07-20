<template>
  <div id="app" class="container">
    <div class="l-inner">
      <div class="l-pageHeader">
        <h1 class="c-heading c-headingLv1">TODOリスト</h1>
      </div><!-- /.l-pageHeader -->
      <div class="l-pageBody">
        <div class="p-todoContent">
          <div class="p-inputTodo">
            <form class="p-addForm">
              <input class="c-inputText"
                type="text"
                name="addName"
                id="addName"
                placeholder="input todo"
                v-model="newItemTitle"
                @keyup.enter="addTodo"
              >
              <div class="p-buttonGroup">
                <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_reset.svg" alt=""></i></button>
                <button class="c-buttonIcon" v-if="this.newItemTitle.length > 0" @click="addTodo"><i class="c-icon"><img src="../assets/image/icon/ic_add.svg" alt=""></i></button>
              </div><!-- /.p-buttonGroup -->
            </form>
          </div><!-- /.p-inputTodo -->
          <ul class="c-list">
            <li v-for="(todo, index) in todos" :key="index" class="c-list_item">
              <label class="c-inputLabel" :class="{ 'todo-is-done': todo.isChecked, }">
                <input class="c-checkbox" type="checkbox" v-model="todo.isChecked" @change="saveTodo">
                <p class="c-inputLabel_text">{{ todo.title }}</p>
              </label>
              <div class="p-buttonGroup">
                <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_edit.svg" alt=""></i></button>
                <button class="c-buttonIcon" @click="removeTodo(index)"><i class="c-icon"><img src="../assets/image/icon/ic_delete.svg" alt=""></i></button>
              </div><!-- /.p-buttonGroup -->
            </li>
          </ul><!-- /.c-list -->
          <div class="p-actionArea">
            <c-button type="primary" @click="showAllTodos">All Tasks</c-button>
            <c-button type="secondary" @click="showActiveTodos">Active</c-button>
            <c-button type="secondary" @click="showCompletedTodos">Completed</c-button>
          </div><!-- /.p-actionArea -->
        </div><!-- /.p-todoContent -->
      </div><!-- /.l-pageBody -->
    </div><!-- /.l-inner -->
  </div><!-- /.container -->
</template>

<script lang="ts">
import Vue from "vue"
import CButton from '@/components/atom/CButton.vue'

export default Vue.extend({
  data: function(){
    return {
      isChecked: false,
      isDelete: false,
      todo: '',
      todos: [
        { title: '', isChecked: true }
      ],
      newItemTitle: ''
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        title: this.newItemTitle,
        isChecked: false
      })
      this.newItemTitle = ''
      this.saveTodo()
    },
    removeTodo(index: number) {
      this.todos.splice(index, 1)
      this.saveTodo()
    },
    showAllTodos() {
      console.log('全部見る')
    },
    showActiveTodos() {
      console.log('まだ終わってないやつ見る')
      this.saveTodo()
    },
    showCompletedTodos() {
      console.log('完了済みのやつ見る')
      this.saveTodo()
    },
    saveTodo() {
      localStorage.setItem('todos', JSON.stringify(this.todos))
    },
    loadTodo() {
      this.todos = JSON.parse(localStorage.getItem('todos'))
      if(!this.todos) {
        this.todos = []
      }
    },
  },
  mounted: function() {
    this.loadTodo();
  }
})
</script>

<style lang="scss">
body {
  background: #ECECF1;
}
.container {
  padding-bottom: 60px;
}
.l-inner {
  max-width: 768px;
  margin: 0 auto;
  padding-right: 16px;
  padding-left: 16px;
}
.l-pageHeader {
  margin-top: 48px;
}
.l-pageBody{
  margin-top: 48px;
}
.p-todoContent {
  box-shadow: 0px 3px 20px rgba(0, 0, 0, 0.45);
  border-radius: 20px;
  padding: 24px;
  background: #fff;
}
.p-inputTodo {
  padding-top: 16px;
  padding-bottom: 16px;
  display: flex;
  border-bottom: solid 1px #E0E0E0;
  .p-buttonGroup {
    margin-left: auto;
  }
}
.p-actionArea {
  margin-top: 64px;
}

.p-addForm {
  width: 100%;
  display: flex;
  .c-inputText{
    flex: 1;
  }
}

// components

.c-buttonIcon {
width: 40px;
padding: 5px;
border: 0;
background: transparent;
img {
  width: 100%;
  vertical-align: bottom;
}
}

.c-list {
  list-style: none;
  padding-left: 0;
  margin-top: 48px;
  .c-list_item {
    margin-top: 32px;
    display: flex;
    &:first-child {
      margin-top: 0;
    }
    .p-buttonGroup {
      margin-left: auto;
    }
  }
}

.c-inputText {
  font-size: 24px;
  width: calc(100% - 120px);
  padding: 8px;
  border: 0;
  &.c-inputText-edit {
    color: #CCC;
  }
}

.c-inputLabel {
  align-items: center;
  position: relative;
  display: inline-block;
  .c-checkbox {
    position: absolute;
    z-index: -1;
    top: 0;
    left: 0;
    opacity: 0;
    &:checked {
      + .c-selectbox_label:after {
        background-color: transparent;
        outline: 0;
      }
      + .c-selectbox_label:before {
        opacity: 1;
      }
      + .c-inputLabel_text {
        &:before {
          opacity: 1;
        }
        &:after {
          background: #FD8170;
          border: 0;
        }
      }
    }
  }
  .c-inputLabel_text {
    position: relative;
    display: block;
    padding-left: 36px;
    cursor: pointer;
    font-size: 24px;
    &:before,
    &:after {
      position: absolute;
    }
    &:before {
      content: "";
      height: 20px;
      left: 9px;
      top: 4px;
      width: 10px;
      border-right: 2px solid #fff;
      border-bottom: 2px solid #fff;
      outline: 0;
      transform: rotate(45deg) translate(-1px,-1px);
      margin: auto;
      opacity: 0;
      z-index: 1;
    }
    &:after {
      content: "";
      left: 0;
      width: 30px;
      height: 30px;
      margin: auto;
      background-color: transparent;
      outline: 0;
      border: 1px solid #979797;
      border-radius: 50%;
    }
  }
}

.todo-is-done {
  text-decoration: line-through;
  color: #FC7867;
  .c-inputLabel_text {
    color: #d8d8d8;
  }
}
.todo-is-delete {
  display: none;
}
</style>