<template>
  <v-container>
    <v-layout wrap align-center justify-center>
      <v-flex xs12 sm6 d-flex>
        <v-select
          :items="sourcesNames"
          label="Selectionner une source"
          v-model="value"
        />
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import axios from "axios";

import { apiKey } from "@/plugins/credentials";

export default {
  data() {
    return {
      sourcesNames: [],
      sourcesIds: [],
      value: ""
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
  updated: function() {
    if (!this.value) {
      return;
    }
    let idx = this.sourcesNames.indexOf(this.value);
    let selectedSource = this.sourcesIds[idx];

    axios
      .get("https://newsapi.org/v2/top-headlines", {
        params: {
          apiKey: apiKey,
          sources: selectedSource
        }
      })
      .then(res => {
        console.log(res);
      })
      .catch(err => console.error(err));
  }
};
</script>

<style></style>
