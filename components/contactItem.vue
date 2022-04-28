<template>
  <div class="contact-list-item">
    <v-card elevation="7">
      <v-row style="padding: 20px 20px 0;">
        <v-col>
          <v-row style="margin-left: 10px">
            <v-col>{{ contact.name }}</v-col>
            <v-col>{{ contact.sname }}</v-col>
            <v-col>{{ contact.patr }}</v-col>
            <v-col>{{ contact.phone }}</v-col>
          </v-row>
        </v-col>

        <v-col @mouseenter="hoverClass = true" @mouseleave="hoverClass = false" class="col-auto prel">
          <svg style="width:50px;height:50px; position:relative; top: -40px;" viewBox="0 0 24 24">
            <path fill="currentColor" d="M7,22H9V24H7V22M11,22H13V24H11V22M15,22H17V24H15V22Z" />
          </svg>
          <nav class="na" v-show="hoverClass">
            <ul style="list-style: none">
              <li>
                <v-btn @click="$emit('delete', contact)">
                  <svg style="width:24px;height:24px" viewBox="0 0 24 24">
                    <path fill="currentColor" d="M9,3V4H4V6H5V19A2,2 0 0,0 7,21H17A2,2 0 0,0 19,19V6H20V4H15V3H9M7,6H17V19H7V6M9,8V17H11V8H9M13,8V17H15V8H13Z" />
                  </svg>
                </v-btn>
              </li>
              <li>
                <v-btn @click="$emit('edit', contact)">
                  <svg style="width:24px;height:24px" viewBox="0 0 24 24">
                    <path fill="currentColor" d="M14.06,9L15,9.94L5.92,19H5V18.08L14.06,9M17.66,3C17.41,3 17.15,3.1 16.96,3.29L15.13,5.12L18.88,8.87L20.71,7.04C21.1,6.65 21.1,6 20.71,5.63L18.37,3.29C18.17,3.09 17.92,3 17.66,3M14.06,6.19L3,17.25V21H6.75L17.81,9.94L14.06,6.19Z" />
                  </svg>
                </v-btn>
              </li>
            </ul>
          </nav>


        </v-col>
      </v-row>

    </v-card>
  </div>
</template>
<script lang="ts">
import {Component, Prop, Vue} from "vue-property-decorator"
@Component
export default class ContactItem extends Vue {
  private hoverClass:boolean = false;
  @Prop ({required:true}) contact!: any
}
</script>

<style>
</style>
