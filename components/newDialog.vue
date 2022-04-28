<template>
  <div class="dialog-wrapper" @click="$emit('closeDialog')">
    <div class="dialog-wrapper-container" @click.stop>
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import {Component, Vue} from "vue-property-decorator";
@Component
export default class NewDialog extends Vue {}
</script>
<style>
.dialog-wrapper {
  display: flex;
  position: fixed;
  width: 100%; height: 100vh;
  top: 0; left: 0;
  right: 0; bottom: 0;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background: #3338;
}
.dialog-wrapper-container {
  padding: 20px;
  border-radius: 10px;
  background: #ffffff;
  min-width: 40px; min-height: 40px;
}
</style>
