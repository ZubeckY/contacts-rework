<template>
  <div>

  </div>
</template>
<script lang="ts">
import {Component, Prop, Vue} from "vue-property-decorator"
@Component
export default class CreateItem extends Vue {
  private hoverClass:boolean = false;
  @Prop ({required:true}) contact!: any
}
</script>

<style scoped>

</style>
