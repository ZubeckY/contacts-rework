<template>
  <div>
    <v-container class="w-100" style="max-width: 1200px;">

      <v-row class="action-buttons">
        <v-col class="col-auto">
          <v-btn elevation="7">Кнопка</v-btn>
        </v-col>
        <v-col class="col-auto">
          <v-btn elevation="7">Кнопка</v-btn>
        </v-col>
      </v-row>

      <div class="contact-list d-flex flex-column" v-for="i in length">
        <contact-item

        />
      </div>
    </v-container>

    <div class="alert-wrapper" v-show="AlertOK">
      <v-alert
        v-if="AlertStatus"
        outlined
        :color="AlertStatusColor"
        :type="AlertStatus"
      >
        <span class="message-text">
          {{AlertValue}}
        </span>
      </v-alert>
    </div>


  </div>
</template>

<!-- success #4caf50 -->
<!-- error #ff5252 -->



<script lang="ts">
import {Component, Vue} from "vue-property-decorator"
import ContactItem from "~/components/contactItem.vue";
@Component({
  components: {ContactItem}
})
export default class Index extends Vue {
  private length:number = 10            //Количество геренации

  private Names:any =   [
    'Имя0',
    'Имя1',
    'Имя2',
    'Имя3',
    'Имя4',
    'Имя5',
    'Имя6',
    'Имя7',
    'Имя8',
    'Имя9'
  ]
  private SNames:any =  [
    'Фамилия0',
    'Фамилия1',
    'Фамилия2',
    'Фамилия3',
    'Фамилия4',
    'Фамилия5',
    'Фамилия6',
    'Фамилия7',
    'Фамилия8',
    'Фамилия9',
  ]
  private Patr:any =    [
    'Отчество0',
    'Отчество1',
    'Отчество2',
    'Отчество3',
    'Отчество4',
    'Отчество5',
    'Отчество6',
    'Отчество7',
    'Отчество8',
    'Отчество9',
  ]

  private Contacts:any= []

  //ALERTS
  private AlertOK:boolean = false
  private dialog:boolean = true


  // Значения
  private AlertValue:string = ''
  private AlertStatus:string = ''
  private AlertStatusColor:any = ''
  // Цвета
  private ErrorColor:string = '#ff5252'
  private SuccessColor:string = '#4caf50'
  // Тип
  private ErrorType:string = 'error'
  private SuccessType:string = 'success'
  // Текста
  private ErrorMessage:string = 'Ошибка'
  private SuccessMessage:string = 'Успешно!'

  generate () {

  }



}
</script>

<style>
.card-container {
  min-height: 80px;
}
.contact-list-item {
  margin: 40px 0;
}
/*position relative*/
.prel {
  position: relative; cursor: pointer;
}
/* кнопки */
.na {
  position: absolute; top: 40px;left: 25px; width: 68px; height: 75px; background: #fff;border: 1px solid #e5e5e5; z-index: 1000000 !important;
}
.alert-wrapper {
  position: fixed; width: 300px; bottom: 10px; right: 10px;;
}
.message-text {
  font-family: "Roboto", sans-serif; margin-left: 15px;
}
</style>
