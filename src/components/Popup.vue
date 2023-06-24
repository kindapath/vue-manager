<template>
  <div class="text-center">
    <v-dialog v-model="dialog" width="600px">
      <template v-slot:activator="{ props }">
        <v-btn color="pink-lighten-1" flat v-bind="props">
          Добавить сотрудника
        </v-btn>
      </template>

      <v-card>
        <v-card-text>
          <v-form class="px-3">
            <v-text-field label="Фамилия" variant="underlined"></v-text-field>
            <v-text-field label="Имя" variant="underlined"></v-text-field>
            <v-text-field label="Отчество" variant="underlined"></v-text-field>
            <v-text-field label="Должность" variant="underlined"></v-text-field>
            <v-checkbox label="Трудовая книжка"></v-checkbox>
            <v-text-field label="Оклад" variant="underlined"></v-text-field>
            <v-date-picker></v-date-picker>
            <v-select label="Ставка" :items="['Полная', 'Половина']"></v-select>
          </v-form>
        </v-card-text>
        <v-card-actions>
          <v-btn color="pink-lighten-1" block @click="dialog = false"
            >Close Dialog</v-btn
          >
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      name: "",
      surname: "",
    };
  },
};
</script>
