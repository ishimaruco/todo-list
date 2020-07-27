<template>
  <button class="c-button" :class="[`c-button-${type}`]" @click="click">
    <slot/>
  </button><!-- /.c-button -->
</template>

<script lang="ts">
import {Component, Vue, Prop, Emit} from 'vue-property-decorator';

@Component({})
export default class CButton extends Vue {
  @Prop({ type: String, default: '' }) type!:string
  @Emit('c-click')
  private click() {}
}
</script>

<style lang="scss">
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
</style>