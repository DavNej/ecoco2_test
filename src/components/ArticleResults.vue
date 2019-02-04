<template>
  <v-item-group>
    <v-container grid-list-md fluid>
      <v-layout wrap>
        <v-flex v-for="article in articles" :key="article.id" xs12 sm6 md4 lg3>
          <v-item>
            <v-card slot-scope="{}" class="d-flex fill-height align-center">
              <v-card class="fill-height">
                
                <!-- Displays default image if no image in article -->
                <v-img
                  v-if="article.urlToImage === null"
                  :src="src"
                  aspect-ratio="2"/>
                <v-img v-else :src="article.urlToImage" aspect-ratio="2" />

                <v-card-title primary-title class="cus__clear-bottom">
                  <div>
                    <h3 class="headline mb-0" v-html="article.title"></h3>
                    <div v-html="article.description"></div>
                  </div>
                </v-card-title>
                <v-card-actions class="cus__position-bottom-right">
                  <v-btn flat color="blue" :href="article.url" target="_blank"
                    >Lire</v-btn
                  >
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
export default {
  name: "articleResults",
  props: {
    articles: {
      type: Array,
      default: null
    }
  },
  data() {
    return { src: require("@/assets/no-image.png") };
  }
};
</script>

<style scoped lang="sass">
.cus__clear-bottom
  padding-bottom: 65px

.cus__position-bottom-right
  position: absolute
  bottom: 0
  right: 0
</style>
