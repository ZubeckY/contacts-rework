<template>
  <div>
    <v-container>
      <v-form>
        <v-row>
          <v-col>
            <v-text-field
              outlined
              label="Название"
              placeholder="Заглушка"
            ></v-text-field>
            <v-btn elevation="7">Кнопка</v-btn>
          </v-col>
          <v-col>
            <v-card elevation="7">
              <div class="card-container"></div>

            </v-card>
          </v-col>
        </v-row>
      </v-form>
    </v-container>

  </div>
</template>

<script lang="ts">

</script>

<style>
.card-container {
  min-height: 80px;
}
</style>
