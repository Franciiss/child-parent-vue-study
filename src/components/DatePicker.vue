<template>
  <div>
    <p>
      {{ texto }}
    </p>
    <v-menu
      v-model="menu2"
      :close-on-content-click="false"
      transition="scale-transition"
      offset-y
      max-width="290px"
      min-width="auto"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-text-field
          v-model="computedDateFormatted"
          :label="label"
          persistent-hint
          prepend-icon="mdi-calendar"
          readonly
          v-bind="attrs"
          v-on="on"
        ></v-text-field>
      </template>
      <v-date-picker
        @change="$emit('update:data', $event)"
        no-title
        @input="menu2 = false"
      ></v-date-picker>
    </v-menu>
  </div>
</template>

<script>
export default {
  name: "datePicker",
  props: ["label", "data"],
  created() {
    if (this.data) {
      this.texto = "Este componente recebeu uma data personalizada";
    } else {
      this.texto = "Este componente NÃO recebeu uma data personalizada";
    }
  },
  data() {
    return {
      texto: "",
      menu1: false,
      menu2: false,
    };
  },
  computed: {
    computedDateFormatted() {
      return this.formatDate(this.data);
    },
  },
  methods: {
    formatDate(date) {
      if (!date) return null;

      const [year, month, day] = date.split("-");
      return `${day}/${month}/${year}`;
    },
  },
};
</script>
