<template>
  <v-container class="pb-0">
    <v-layout wrap align-center justify-center>
      <v-flex xs12 sm6 d-flex>
        <v-select
          :items="sourcesNames"
          label="Selectionner une source"
          v-model="selectedSource"
        />
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import axios from "axios";

import { apiKey } from "@/plugins/credentials";

export default {
  name: 'FormSelect',
  data() {
    return {
      sourcesNames: [],
      sourcesIds: [],
      selectedSource: ""
    };
  },
  created: function() {
    axios
      .get("https://newsapi.org/v2/sources", {
        params: {
          apiKey: apiKey,
          language: "fr",
          country: "fr"
        }
      })
      .then(res => {
        this.sourcesNames = res.data.sources.map(element => element.name);
        this.sourcesIds = res.data.sources.map(element => element.id);
      })
      .catch(err => console.error(err));
  },
  watch: {
    selectedSource: function() {
      let idx = this.sourcesNames.indexOf(this.selectedSource);
      let selectedSourceId = this.sourcesIds[idx];

      axios
        .get("https://newsapi.org/v2/top-headlines", {
          params: {
            apiKey: apiKey,
            sources: selectedSourceId
          }
        })
        .then(res => {
          if (res.status === 200) {
            this.$emit('sourceIsSelected', res.data);
          } else {
            alert('Une erreur s\'est produite, veuillez réessayer')
            console.error(res)
          }
        })
        .catch(err => console.error(err));
    }
  }
};
</script>

<style></style>
