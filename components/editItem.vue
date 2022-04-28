<template>
  <div>
    <v-card style="width: 320px; height: 370px;">
      <h4 style="text-align: center; padding: 10px;">Редактировать</h4>
      <div>

        <v-text-field
          placeholder="Имя"
          style="width: 280px; margin: 3px auto"
          :value="contact.name"
          solo
        />
        <v-text-field
          placeholder="Фамилия"
          style="width: 280px; margin: 3px auto"
          :value="contact.sname"
          solo
        />
        <v-text-field
          placeholder="Телефон"
          type="number"
          style="width: 280px; margin: 3px auto"
          :value="contact.phone"
          solo
        />

      </div>
      <div style="display:flex; justify-content:space-around; margin-top: 20px">
        <v-btn @click="logger">Редактировать</v-btn>
        <v-btn @click="$emit ('closeDialog')">Отмена</v-btn>
      </div>
    </v-card>
  </div>
</template>
<script lang="ts">
import {Component, Prop, Vue} from "vue-property-decorator"
@Component
export default class EditItem extends Vue {
  @Prop ({required:true}) contact!: any
  private hoverClass:boolean = false;

  logger () {
    console.log(this.contact)
  }
  // this.$emit('editContact', this.contact)

}
</script>

<style>
</style>
