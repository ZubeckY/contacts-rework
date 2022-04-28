<template>
  <div>
    <v-container class="w-100" style="max-width: 1200px;">
      <v-row class="action-buttons">
        <v-col class="col-auto">
          <v-btn elevation="7" @click="generate">{{ Contacts.length ? 'ЕЩЁ ГЕНЫ' : 'ГЕНА'}}</v-btn>
        </v-col>
        <v-col class="col-auto">
          <v-btn elevation="7" @click="CreateNewElem">Добавить</v-btn>
        </v-col>
      </v-row>
      <header>
        <v-row style="padding: 20px 20px 0;">
          <v-col>
            <v-row style="margin-left: 10px">
              <v-col>Имя</v-col>
              <v-col style="margin-left: 50px" >Фамилия</v-col>
              <v-col style="margin-left: 50px" >Тел</v-col>
              <v-col class="col-auto">Количество: {{Contacts.length}}</v-col>
            </v-row>
          </v-col>
        </v-row>
      </header>
      <div class="contact-list d-flex flex-column" v-for="contact in Contacts">
        <contact-item
          :contact="contact"
          :key="contact.id"
          @delete="AskDeleteItem (contact)"
          @edit="ShowEditWindow (contact)"
        />
      </div>
    </v-container>

    <new-dialog
      v-show="dialog"
      @closeDialog='closeDialog'
    >
      <div v-if="condition == 'create'">
        <create-item
          @createContact ='createContact'
          @closeDialog='closeDialog'
        />
      </div>
      <div v-else-if="condition == 'edit'">
        <edit-item
          :contact="contact"
          :key="contact.id"
          @editContact="editContact"
          @closeDialog='closeDialog'
        />
      </div>
      <div v-else-if="condition == 'ask'">
        <ask-delete-item
          :contact="contact"
          :key="contact.id"
          @removeContact = 'removeContact (contact)'
          @closeDialog = 'closeDialog'
        />
      </div>
    </new-dialog>

    <div class="alert-wrapper" v-show="AlertOK">
      <v-alert
        outlined
        v-if="AlertStatus"
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
<script lang="ts">
import {Component, Vue} from "vue-property-decorator"
import ContactItem from "~/components/contactItem.vue";
import NewDialog from "~/components/newDialog.vue";
import CreateItem from "~/components/createItem.vue";
import AskDeleteItem from "~/components/askDeleteItem.vue";
import EditItem from "~/components/editItem.vue";
@Component({
  components: {EditItem, AskDeleteItem, CreateItem, NewDialog, ContactItem}
})
export default class Index extends Vue {
  private length:number = 10            // Количество геренации
  private condition:string = ''         // Что будет выводить диалог

  private Names:any    =   [
    'Имя 0',
    'Имя 1',
    'Имя 2',
    'Имя 3',
    'Имя 4',
    'Имя 5',
    'Имя 6',
    'Имя 7',
    'Имя 8',
    'Имя 9'
  ]
  private SNames:any   =   [
    'Фамилия 0',
    'Фамилия 1',
    'Фамилия 2',
    'Фамилия 3',
    'Фамилия 4',
    'Фамилия 5',
    'Фамилия 6',
    'Фамилия 7',
    'Фамилия 8',
    'Фамилия 9',
  ]

  private Contacts:any =   []
  private contact:any  =   {}

  //ALERTS
  private AlertOK:boolean = false
  private dialog:boolean = false

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
      let getRandom = (min:any, max:any) => {return Math.floor(Math.random() * (max-min) + min)}
      let index = getRandom (0, this.length)

      let name:any = this.Names[index]
      let sname:any = this.SNames[index]
      let phone:any

      let item = {
        name: name,
        sname: sname,
        phone: (Math.round (Math.random() * 100000000000)),
        id: name + (Math.round (Math.random() * 100000)) + sname,
      }
      this.Contacts.push (item)
    }
  }
  createContact (contact:any) {
    this.closeDialog()
    this.Contacts.push (contact)
  }
  editContact (contact:any) {
    this.contact = contact
    this.closeDialog()
    return this.Contacts
  }
  removeContact (contact:any) {
    this.closeDialog()
    this.Contacts = this.Contacts.filter ((cont:any) => cont.id != contact.id)
  }
  // Какую модалку высвечивать
  CreateNewElem () {
    this.condition = 'create'
    this.dialog = true
  }
  AskDeleteItem (item:any) {
    this.contact = item;
    this.condition = 'ask'
    this.dialog = true
  }
  ShowEditWindow (item:any) {
    this.contact = item;
    this.condition = 'edit'
    this.dialog = true;
  }

  closeDialog () {
    this.dialog = false;
    this.contact = {
      name: 'SS',
      sname: 'SS',
      phone: 'SS',
      id: 'SS',
    }
    this.condition = ''
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
  position: absolute; top: 40px;left: 25px; width: 68px; height: 75px; background: #fff; border: 1px solid #e5e5e5; z-index: 1000000 !important;
}
.alert-wrapper {
  position: fixed; width: 300px; bottom: 10px; right: 10px;;
}
.message-text {
  font-family: "Roboto", sans-serif; margin-left: 15px;
}
</style>
