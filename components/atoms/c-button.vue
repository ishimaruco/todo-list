<template>
    <button class="c-button"  @click="click">
        <slot/>
    </button><!-- /.c-button -->
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'CButton',
});
</script>

<style lang="scss" module>
.c-button {
  
}
</style>