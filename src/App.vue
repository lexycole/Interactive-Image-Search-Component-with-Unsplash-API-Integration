<template>
    <v-app>
     <v-main>

    <!-- 01 Header Input Screen -->
      <v-card
        color="grey lighten-3">
          <v-form @submit.prevent="getData">
            <v-container 
                  class="spacing-playground pa-16"
                  fluid>
              <v-row>
                <v-col
                  cols="12"
                  sm="12" >
                  <v-text-field
                      solo
                      label="Search for photo..."
                      prepend-inner-icon="mdi-magnify"
                      v-model="topic">
                  </v-text-field>
                </v-col>
              </v-row>

               <v-card color="#DDE2E9" class="d-flex justify-center mb-1"  
                 v-if="firstLoadSearch">
                  <p class="text-h4 text--primary">
                   Searching for"{{topic}}"
                  </p> 
              </v-card>
              <v-card color="#DDE2E9" class="d-flex justify-center mb-1"  
                v-if="!firstLoadSearch">
                  <p class="text-h4 text--primary">
                   Search Results for "{{topic}}"
                  </p>
              </v-card> 
              
            </v-container>
          </v-form>
    </v-card>

     <!-- 02. First loading Screen -->
      <v-container v-if="firstScreen">
         <v-sheet
            :color="`grey ${theme.isDark ? 'darken-2' : 'lighten-4'}`"
            class="pa-10" v-if="firstLoad">
            <v-row>
            <v-col
                cols="12"
                md="4">
                  <v-skeleton-loader
                    class="mx-auto"
                    max-width="300"
                    type="card">
                  </v-skeleton-loader>
            </v-col>
            <v-col
                cols="12"
                md="4">
              <v-skeleton-loader
                  class="mx-auto"
                  max-width="300"
                  type="card" >
              </v-skeleton-loader>
            </v-col>
            <v-col
                cols="12"
                md="4">
            <v-skeleton-loader
                class="mx-auto"
                max-width="300"
                type="card">
                </v-skeleton-loader>
            </v-col>
            </v-row>

            <v-row>
            <v-col
                cols="12"
                md="4">
                  <v-skeleton-loader
                    class="mx-auto"
                    max-width="300"
                    type="card">
                  </v-skeleton-loader>
            </v-col>
            <v-col
                cols="12"
                md="4" >
              <v-skeleton-loader
                  class="mx-auto"
                  max-width="300"
                  type="card" >
              </v-skeleton-loader>
            </v-col>
            <v-col
                cols="12"
                md="4">
            <v-skeleton-loader
                class="mx-auto"
                max-width="300"
                type="card">
                </v-skeleton-loader>
            </v-col>
            </v-row>    
        </v-sheet>

        <v-container class="mt-n15 mx-auto" v-if="!firstLoad">
            <v-row>
            <v-col
                cols="auto"
                md="4" 
                v-for="(image, i) in images"
                        :key="i">
                <v-card width="300"
                      class="mx-auto"
                    @click="dialog = true">
                <v-img
                  height="400px"
                  :src="image.urls.small" :alt="image.alt_description"
                  class="img-bg">
                </v-img>
                <div class="card-detail mb-4 ml-2">
                    {{ image.user.name }}
                <p>{{ image.user.location }}</p>
                </div>
                <div class="overlay-image"></div>
                </v-card>
            </v-col>

            </v-row>
        </v-container>

          <div>
            <v-row justify="center" >
                  <v-dialog
                        v-model="dialog"
                        max-width="600px">
                        <v-card>
                            <v-img
                              height="300px"
                              class="grey darken-4"
                               src="https://picsum.photos/350/165?random" />
                            <v-card-title class="author-size">
                              image.user.name
                            </v-card-title>
                            <v-card-title class="mt-n5">
                        <p class="location-size">
                          image.user.location
                        </p>
                        </v-card-title>
                        
                        <v-card-actions class="justify-end">
                            <v-btn
                            color="primary"
                            text
                            @click="dialog = false" >
                            close
                            </v-btn>
                        </v-card-actions>
                        </v-card>
                  </v-dialog>
                  </v-row>
            </div>
      </v-container>

    <!-- 03. Search Results Screen -->
    <v-container v-if="!firstScreen">
        <v-sheet
            :color="`grey ${theme.isDark ? 'darken-2' : 'lighten-4'}`"
            class="pa-10" v-if="firstLoad">
            <v-row>
            <v-col
                cols="12"
                md="4">
                  <v-skeleton-loader
                    class="mx-auto"
                    max-width="300"
                    type="card">
                  </v-skeleton-loader>
            </v-col>
            <v-col
                cols="12"
                md="4" >
              <v-skeleton-loader
                  class="mx-auto"
                  max-width="300"
                  type="card" >
              </v-skeleton-loader>
            </v-col>
            <v-col
                cols="12"
                md="4">
            <v-skeleton-loader
                class="mx-auto"
                max-width="300"
                type="card">
                </v-skeleton-loader>
            </v-col>
            </v-row>
            <v-row>
            <v-col
                cols="12"
                md="4">
                  <v-skeleton-loader
                    class="mx-auto"
                    max-width="300"
                    type="card">
                  </v-skeleton-loader>
            </v-col>
            <v-col
                cols="12"
                md="4" >
              <v-skeleton-loader
                  class="mx-auto"
                  max-width="300"
                  type="card" >
              </v-skeleton-loader>
            </v-col>
            <v-col
                cols="12"
                md="4">
            <v-skeleton-loader
                class="mx-auto"
                max-width="300"
                type="card">
                </v-skeleton-loader>
            </v-col>
            </v-row>    
        </v-sheet>

        <v-container class="mt-n15 mx-auto" v-show="!firstLoad">
            <v-row>
            <v-col
                cols="auto"
                md="4" 
                v-for="(image, i) in images"
                        :key="i">
                <v-card width="300"
                      class="mx-auto"
                    @click="dialog = true">
                <v-img
                  height="400px"
                  :src="image.urls.small" :alt="image.alt_description"
                  class="img-bg">
                </v-img>
                <div class="card-detail mb-4 ml-2">
                    {{ image.user.name }}
                <p>{{ image.user.location }}</p>
                </div>
                <div class="overlay-image"></div>
                </v-card>
            </v-col>

            </v-row>
        </v-container>

          <div>
            <v-row justify="center" >
                  <v-dialog
                        v-model="dialog"
                        max-width="600px">
                        <v-card>
                            <v-img
                            src="https://picsum.photos/350/165?random"
                            height="300px"
                            class="grey darken-4"
                            ></v-img>
                            <v-card-title class="author-size">
                            Fredrick Apata
                            </v-card-title>
                            <v-card-title class="mt-n5">
                        <p class="location-size">Lagos, Nigeria</p>
                        </v-card-title>
                        
                        <v-card-actions class="justify-end">
                            <v-btn
                            color="primary"
                            text
                            @click="dialog = false" >
                            close
                            </v-btn>
                        </v-card-actions>
                        </v-card>
                  </v-dialog>
            </v-row>
        </div>

    </v-container>
    </v-main>
    </v-app>
</template>



    <script>
        import axios from "axios";

        export default {
          name: 'App',
            inject: {
              theme: {
                default: { isDark: false },
              },
            }, 
            components: {
            },
            data: () => ({
              firstLoad: true,
              firstLoadSearch: true,
              dialog: false,
              firstScreen: true,
              topic: "",
              images: [], 
            }),
              mounted(username, location) {
                  axios
                      .get(
                        `https://api.unsplash.com/search/photos/?query=African&${username}&${location}[name]&per_page8`,
                        {
                            headers: {
                              Authorization:
                                "Client-ID sjBs1QT-YfeOktwp6LQ--sGS-Jn4b2-k_Ggs3GkGGP0",
                                "Accept-Version": "v1"
                            },
                          }
                        )
                        .then(response => {
                          this.images = response.data.results;
                        })
                        .catch(() => {
                          this.images = []
                        })
                        ,
                      setTimeout(() => {
                          if (this.firstLoad ) 
                            this.firstLoad = false
                          }, 1000);
                  },

              methods: {
                    async getData(username, location) {
                        await axios
                          .get(
                            `https://api.unsplash.com/search/photos/?query=${this.topic}&${username}&${location}[name]&per_page8`,
                            {  headers: {
                                  Authorization:
                                    "Client-ID sjBs1QT-YfeOktwp6LQ--sGS-Jn4b2-k_Ggs3GkGGP0",
                                    "Accept-Version": "v1"
                                },
                              }
                            )
                            .then(response => {
                              this.images = response.data.results;
                            })
                            .catch(() => {
                              this.images = [];
                            });
                        setTimeout(() => {
                          if (this.firstLoad || this.firstLoadSearch)  
                            this.firstLoad = false;
                            this.firstLoadSearch = false;
                        }, 1000);
                  },
              },
            };
      </script>



  <style>
    .card-detail {
          padding: 0 20px;
          position: absolute;
          bottom: 0;
          color: #fff;
          font-size: 20px;
      }
      .card-detail p {
          color: #fff;
          font-size: 15px;
      }
      .overlay-image {
        left: 0;
        bottom:0;
        right:0;
        width: 100%;
        height: 40%;
        position: absolute;
        border-radius: 180px;
        background-image: url("https://images.app.goo.gl/BYkD2WBt29nM3sDi9");
        background-image: linear-gradient(
          to bottom,
          hsla(0, 0%, 0%, 0) 0%,
          hsla(0, 0%, 0%, 0.009) 11.7%,
          hsla(0, 0%, 0%, 0.034) 22.1%,
          hsla(0, 0%, 0%, 0.072) 31.2%,
          hsla(0, 0%, 0%, 0.123) 39.4%,
          hsla(0, 0%, 0%, 0.182) 46.6%,
          hsla(0, 0%, 0%, 0.249) 53.1%,
          hsla(0, 0%, 0%, 0.320) 58.9%,
          hsla(0, 0%, 0%, 0.394) 64.3%,
          hsla(0, 0%, 0%, 0.468) 69.3%,
          hsla(0, 0%, 0%, 0.540) 74.1%,
          hsla(0, 0%, 0%, 0.607) 78.8%,
          hsla(0, 0%, 0%, 0.668) 83.6%,
          hsla(0, 0%, 0%, 0.721) 88.7%,
          hsla(0, 0%, 0%, 0.762) 94.1%,
          hsla(0, 0%, 0%, 0.790) 100%
        );
          opacity: .7;
      }
      .location-size {
          font-size: 15px
      } 
        </style>