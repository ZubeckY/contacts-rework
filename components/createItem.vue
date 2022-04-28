<template>
  <div>
    <v-card style="width: 320px; height: 370px;">
      <h4 style="text-align: center; padding: 10px;">Добавить</h4>
      <div>

        <v-text-field
          placeholder="Имя"
          style="width: 280px; margin: 3px auto"
          v-model:value="contact.name"
          solo
        />
        <v-text-field
          placeholder="Фамилия"
          style="width: 280px; margin: 3px auto"
          v-model:value="contact.sname"
          solo
        />
        <v-text-field
          placeholder="Телефон"
          type="number"
          style="width: 280px; margin: 3px auto"
          v-model:value="contact.phone"
          solo
        />

      </div>
      <div style="display:flex; justify-content:space-around; margin-top: 20px">
        <v-btn @click="Check">Добавить</v-btn>
        <v-btn @click="$emit ('closeDialog')">Отмена</v-btn>
      </div>
    </v-card>
  </div>
</template>
<script lang="ts">
import {Component, Vue} from "vue-property-decorator"
@Component
export default class CreateItem extends Vue {
  private hoverClass:boolean = false;

  private contact:any = {
    name: '',
    sname: '',
    phone: '',
    id: '',
  }
  Check () {
    this.contact.id = this.contact.name + (Math.round (Math.random() * 100000)) + this.contact.sname,
    this.$emit('createContact', this.contact)
  }
}
</script>

<style>
</style>
