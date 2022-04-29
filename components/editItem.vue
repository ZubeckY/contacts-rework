<template>
  <div>
    <v-card style="width: 320px; height: 370px;">
      <h4 style="text-align: center; padding: 10px;">Редактировать</h4>
      <div>
        <v-text-field
          placeholder="Имя"
          style="width: 280px; margin: 3px auto"
          v-model:value="contacter.name"
          solo
        />
        <v-text-field
          placeholder="Фамилия"
          style="width: 280px; margin: 3px auto"
          v-model:value="contacter.sname"
          solo
        />
        <v-text-field
          placeholder="Телефон"
          type="number"
          style="width: 280px; margin: 3px auto"
          v-model:value="contacter.phone"
          solo
        />
      </div>
      <div style="display:flex; justify-content:space-around; margin-top: 20px">
        <v-btn @click="checkValues">Редактировать</v-btn>
        <v-btn @click="$emit ('closeDialog')">Отмена</v-btn>
      </div>
    </v-card>
  </div>
</template>
<script lang="ts">
import {Component, Prop, Watch, Vue} from "vue-property-decorator"
@Component
export default class EditItem extends Vue {
  @Prop ({required:true}) contact!: any
  private contacter:any = {}

  @Watch('contact', {immediate: true, deep: true})
  watchLogger(v:any) {
    for (let key in this.contact) {
      this.contacter[key] = this.contact[key];
    }
  }
  checkValues () {
    this.$emit ('editContact', this.contacter)
  }
}
</script>

<style>
</style>
