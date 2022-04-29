<template>
  <div>
    <v-card style="width: 320px; min-height: 200px;">
      <h4 style="text-align: center; padding: 10px;">Вы действительно хотите удалить?</h4>
      <div style="margin: 20px">
        <div style="margin: 10px 0"><strong>id:</strong> {{contact.id}}  </div>
        <div style="margin: 10px 0"><strong>Имя:</strong> {{contact.name}}  </div>
        <div style="margin: 10px 0"><strong>Тел:</strong> {{contact.phone}} </div>
      </div>
      <div style="display:flex; justify-content:space-around; margin-top: 20px">
        <v-btn @click="$emit ('removeContact', contact)">Удалить</v-btn>
        <v-btn @click="$emit ('closeDialog')">Отмена</v-btn>
      </div>
    </v-card>
  </div>
</template>
<script lang="ts">
import {Component, Prop, Vue} from "vue-property-decorator"
@Component
export default class AskDeleteItem extends Vue {
  @Prop ({required:true}) contact!: any
}
</script>

<style>
</style>
