<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />
      </div>
    </v-app-bar>

    <v-main>
      <v-row>
        <v-col>
          <DatePicker
            ref="dataInicio"
            label="Data Inicio"
            :data.sync="dataInicio"
          />
        </v-col>
        <v-col>
          <DatePicker ref="dataFim" :data.sync="dataFim" label="Data Fim" />
        </v-col>
      </v-row>
      <br />

      <v-row class="mt-2">
        <v-col>
          <p>Data Inicial: {{ dataInicio }}</p>
          <p>Data Final: {{ dataFim }}</p>
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import DatePicker from "./components/DatePicker";

export default {
  name: "App",

  components: {
    DatePicker,
  },
  data: () => ({
    dataInicio: null,
    dataFim: new Date(
      new Date().getTime() +
        24 * 60 * 60 * 1000 -
        new Date().getTimezoneOffset() * 60000
    )
      .toISOString()
      .substr(0, 10),
  }),
  methods: {
    // Maneira de acessar programaticamente os dados dos componentes filhos definidos pelo ref no template
    submit() {
      this.formulario.dataInicio = this.$refs.dataInicio.data;
      this.formulario.dataFim = this.$refs.dataFim.data;
    },
  },
};
</script>
