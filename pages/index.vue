<template>
  <div class="container">
    <div class="l-inner">
      <div class="l-pageHeader">
        <h1 class="c-heading c-headingLv1">TODOリスト</h1>
      </div><!-- /.l-pageHeader -->
      <div class="l-pageBody">
        <div class="p-todoContent">
          <div class="p-inputTodo">
            <input class="c-inputText" type="text" name="addName" id="addName" placeholder="input todo">
            <div class="p-buttonGroup">
              <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_reset.svg" alt=""></i></button>
              <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_add.svg" alt=""></i></button>
            </div><!-- /.p-buttonGroup -->
          </div><!-- /.p-inputTodo -->
          <ul class="c-list">
            <li class="c-list_item">
              <input class="c-inputText" type="text">
              <div class="p-buttonGroup">
                <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_edit.svg" alt=""></i></button>
                <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_delete.svg" alt=""></i></button>
              </div><!-- /.p-buttonGroup -->
            </li>
            <li class="c-list_item">
              <input class="c-inputText" type="text">
              <div class="p-buttonGroup">
                <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_edit.svg" alt=""></i></button>
                <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_delete.svg" alt=""></i></button>
              </div><!-- /.p-buttonGroup -->
            </li>
            <li class="c-list_item">
              <input class="c-inputText" type="text">
                <div class="p-buttonGroup">
                  <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_edit.svg" alt=""></i></button>
                  <button class="c-buttonIcon"><i class="c-icon"><img src="../assets/image/icon/ic_delete.svg" alt=""></i></button>
              </div><!-- /.p-buttonGroup -->
            </li>
          </ul><!-- /.c-list -->
          <div class="p-actionArea">
            <button class="c-button c-button-primary">All Tasks</button>
            <button class="c-button c-button-secondary">Active</button>
            <button class="c-button c-button-secondary">Completed</button>
          </div><!-- /.p-actionArea -->
        </div><!-- /.p-todoContent -->
      </div><!-- /.l-pageBody -->
    </div><!-- /.l-inner -->
  </div><!-- /.container -->
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({})
</script>

<style lang="scss">
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

// components
.c-button {
border: 0;
background: transparent;
padding-top: 16px;
padding-bottom: 16px;
min-width: 150px;
text-align: center;
font-weight: 700;
box-sizing: border-box;
border-radius: 100px;
&.c-button-primary {
  background: #FD8C7C;
  color: #fff;
}
&.c-button-secondary {
  background: #fff;
  border: solid 1px #BDBDBD;
}
}

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
}
</style>