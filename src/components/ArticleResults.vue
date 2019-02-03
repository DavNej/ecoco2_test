<template>
  <v-item-group>
    <v-container grid-list-md fluid>
      <v-layout wrap>
        <v-flex
          v-for="article in articles"
          :key="article.id"
          xs12
          sm6
          md4
          lg3>
          <v-item>
            <v-card
              slot-scope="{ active, toggle }"
              class="d-flex align-center">
              <v-card>
                  <!-- height="320" -->
                <v-img
                  :src="article.urlToImage"
                  aspect-ratio="2"/>

                <v-card-title primary-title>
                  <div>
                    <h3 class="headline mb-0" v-html="article.title"></h3>
                    <div v-html="article.description"></div>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-btn flat color="blue" :href="article.url" target="_blank">Lire</v-btn>
                </v-card-actions>
              </v-card>
            </v-card>
          </v-item>
        </v-flex>
      </v-layout>
    </v-container>
  </v-item-group>
</template>

<script>
import axios from "axios";

import { apiKey } from "@/plugins/credentials";

export default {
  name: 'articleResults',
  props: {
    articles: {
      type: Array,
      default: []
    }
  }
};
</script>

<style></style>
