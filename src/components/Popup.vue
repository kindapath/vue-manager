<template>
  <div class="text-center">
    <v-dialog v-model="dialog" width="600px">
      <template v-slot:activator="{ props }">
        <v-btn icon flat v-bind="props">
          <slot name="btn-icon"></slot>
        </v-btn>
      </template>
      <v-card>
        <v-card-text>
          <v-form class="px-3" ref="form">
            <v-text-field
              label="Фамилия"
              variant="underlined"
              v-model="surname"
              :rules="[rules.required]"
            ></v-text-field>

            <v-text-field
              label="Имя"
              variant="underlined"
              v-model="name"
              :rules="[rules.required]"
            >
            </v-text-field>

            <v-text-field
              label="Отчество"
              variant="underlined"
              v-model="middleName"
              :rules="[rules.required]"
            ></v-text-field>

            <v-text-field
              label="Должность"
              variant="underlined"
              v-model="job"
              :rules="[rules.required]"
            ></v-text-field>

            <v-checkbox label="Трудовая книжка" v-model="book"></v-checkbox>

            <v-text-field
              label="Оклад"
              variant="underlined"
              v-model="salary"
              :rules="[rules.numberRule]"
            ></v-text-field>

            <v-text-field
              :value="enterDate"
              label="Дата выхода на работу"
              variant="underlined"
              type="date"
              v-model="enterDate"
              :rules="[rules.required]"
            ></v-text-field>

            <v-select
              label="Ставка"
              v-model="pay"
              :items="['Полная', 'Половина']"
              :rules="[rules.required]"
            ></v-select>
          </v-form>
        </v-card-text>

        <!-- submit button -->
        <v-card-actions>
          <v-btn
            v-if="this.edit"
            color="pink-lighten-1"
            block
            @click="submitEdit"
          >
            Редактировать</v-btn
          >
          <v-btn v-else color="pink-lighten-1" block @click="submit">
            Добавить</v-btn
          >
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import { format } from "date-fns";
import { ru } from "date-fns/locale";
import { toRaw } from "vue";

export default {
  props: {
    edit: {
      type: [Boolean],
    },
    employeeInfo: {
      type: [Object],
    },
    employeeIndex: {
      type: [Number],
    },
    btn: {
      type: [String],
    },
  },
  data() {
    return {
      dialog: false,
      name: "",
      surname: "",
      middleName: "",
      job: "",
      book: false,
      salary: "",
      enterDate: null,
      pay: "",
      rules: {
        inputRules: [
          (v) => v.length >= 2 || "Минимальное количество символов - 2",
        ],
        required: (value) => !!value || "Это обязательное поле",
        numberRule: (v) => {
          if (!v.trim()) return true;
          if (!isNaN(parseFloat(v)) && v >= 0) return true;
          return "Невалидное число";
        },
      },
    };
  },
  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        const employee = {
          name: this.name,
          surname: this.surname,
          middleName: this.middleName,
          job: this.job,
          book: this.book,
          salary: this.salary,
          enterDate: this.enterDate,
          pay: this.pay,
        };
        this.$emit("addItem", employee);
      }
    },
    submitEdit() {
      if (this.$refs.form.validate()) {
        const employee = {
          name: this.name,
          surname: this.surname,
          middleName: this.middleName,
          job: this.job,
          book: this.book,
          salary: this.salary,
          enterDate: this.enterDate,
          pay: this.pay,
        };
        this.$emit("editItem", employee, this.employeeIndex);
      }
    },
  },
  computed: {
    formattedDate() {
      return this.enterDate
        ? format(new Date(this.enterDate), "do MMM yyyy", { locale: ru })
        : "";
    },
  },
};
</script>
