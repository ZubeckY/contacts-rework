<template>
  <div>
    РЕДАКТИРОВАТЬ
  </div>
</template>
<script lang="ts">
import {Component, Prop, Vue} from "vue-property-decorator"
@Component
export default class EditItem extends Vue {
  private hoverClass:boolean = false;
  @Prop ({required:true}) contact!: any
}
</script>

<style>
</style>
