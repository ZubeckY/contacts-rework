<template>
  <div>
    <v-container class="w-100" style="max-width: 1200px;">
      <v-row class="action-buttons">
        <v-col class="col-auto">
          <v-btn elevation="7" @click="generate">{{ Contacts.length ? 'ЕЩЁ ГЕНЫ' : 'ГЕНА'}}</v-btn>
        </v-col>
        <v-col class="col-auto">
          <v-btn elevation="7">Добавить</v-btn>
        </v-col>
      </v-row>
      <header>
        <v-row style="padding: 20px 20px 0;">
          <v-col>
            <v-row style="margin-left: 10px">
              <v-col>Имя</v-col>
              <v-col style="margin-left: -80px" >Фамилия</v-col>
              <v-col style="margin-left: -70px" >Отчество</v-col>
              <v-col style="margin-left: -100px" >Тел</v-col>
            </v-row>
          </v-col>
        </v-row>
      </header>
      <div style="margin-top: 15px">
        Количество: {{Contacts.length}}
      </div>
      <div class="contact-list d-flex flex-column" v-for="contact in Contacts">
        <contact-item
          :contact="contact"
          @delete="AskDeleteItem (contact)"
          @edit="ShowEditWindow (contact)"

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
  private contact:any = []

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
    for (let i = 0; i < this.length; i++) {
      let getRandom = (min, max) => {return Math.floor(Math.random() * (max-min) + min)}
      let index = getRandom (0, this.length)

      let nam:any = this.Names[index]
      let snam:any = this.SNames[index]
      let partn:any = this.Patr[index]

      let item = {
        name: nam,
        sname: snam,
        patr: partn,
        phone: Math.round (Math.random() * 100000000000),
      }
      this.Contacts.push (item)
    }
  }

  AskDeleteItem (item) {
    this.contact = item;
  }

  ShowEditWindow (item) {
    this.contact = item;
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
