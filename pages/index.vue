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

      <div class="contact-list d-flex flex-column">

        <div class="contact-list-item">
          <v-card elevation="7">
            <v-row style="padding: 20px">
              <v-col>Content</v-col>
              <v-col class="col-auto">
                <v-btn >Actions</v-btn>
              </v-col>
            </v-row>
          </v-card>
        </div>

        <div class="contact-list-item">
          <v-card elevation="7">
            <v-row style="padding: 20px">
              <v-col>Content</v-col>
              <v-col class="col-auto">
                <v-btn >Actions</v-btn>
              </v-col>
            </v-row>
          </v-card>
        </div>


      </div>


    </v-container>

  </div>
</template>

<script lang="ts">

</script>

<style>
.card-container {
  min-height: 80px;
}

.contact-list {

}
.contact-list-item {
  margin: 40px 0;
}

</style>
