<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline">
        <span>Give me News</span>
      </v-toolbar-title>
    </v-toolbar>

    <v-content>
      <form-select />
    </v-content>
  </v-app>
</template>

<script>
import FormSelect from "./components/FormSelect";

export default {
  name: "App",
  components: {
    FormSelect
  },
  data() {
    return {
      //
    };
  }
};
</script>
