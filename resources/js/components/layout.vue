<template>
  <v-app id="inspire">
      
    <v-navigation-drawer
      v-model="drawerRight"
      app
      clipped
      right
    >
      <v-list dense>
        <v-list-item @click.stop="right = !right">
          <v-list-item-action>
            <v-icon>mdi-exit-to-app</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>باز کردن</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      clipped-right
      color="blue-grey"
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>{{title}}</v-toolbar-title>
      <v-spacer />
      <v-app-bar-nav-icon @click.stop="drawerRight = !drawerRight" />
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list dense>
        <v-list-item @click.stop="left = !left">
          <v-list-item-action>
            <v-icon>mdi-exit-to-app</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Open Temporary Drawer</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-navigation-drawer
      v-model="left"
      fixed
      temporary
    />
    <v-content>
      <v-container
        class="fill-height"
        fluid
      >
      
        <v-row
          justify="center"
          align="center"
        >
          <v-col class="shrink">
              <h1 @click="randomNumber(10)">{{a}}</h1>
            <!-- <v-tooltip right>
              <template v-slot:activator="{ on }">
                <v-btn
                  :href="source"
                  icon
                  large
                  target="_blank"
                  v-on="on"
                >
                  <v-icon large>mdi-code-tags</v-icon>
                </v-btn>
              </template>
              <span>Source</span>
            </v-tooltip>
            <v-tooltip right>
              <template v-slot:activator="{ on }">
                <v-btn
                  icon
                  large
                  href="https://codepen.io/johnjleider/pen/QewYYx"
                  target="_blank"
                  v-on="on"
                >
                  <v-icon large>mdi-codepen</v-icon>
                </v-btn>
              </template>
              <span>Codepen</span>
            </v-tooltip> -->
          </v-col>
        </v-row>
      </v-container>
    </v-content>

    <v-navigation-drawer
      v-model="right"
      fixed
      right
      temporary
    />

    <v-footer
      app
      color="blue-grey"
      class="white--text"
    >
      <span>{{title}}</span>
      <v-spacer />
      <span>&copy; 2020</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    props: {
      source: String,
        n:'',
        a:[]
    },
    data: () => ({
      drawer: null,
      drawerRight: null,
      right: false,
      left: false,
        title:document.title,
    }),
      methods: {
          changeRTL () {
              this.$vuetify.rtl = true
          },
          randomNumber(d){
              let x;

              for (let i=0;i<d;i++){
                  x = Math.floor(Math.random() * 10);
                  this.a = this.a.push('as');
              }
              
          },
          getRandomArbitrary(max) {
              let l = String(max).length;
              let min = 0;
              min = Math.ceil(min);
              max = Math.floor(max);
              let i = Math.floor(Math.random() * (max - min + 1)) + min; //The maximum is inclusive and the minimum is inclusive
              let n;
              if (String(i).length<l){
                  let zero = '0';
                  let x = l - String(i).length;
                  n = i.toString();
                  for (i=0;i<x;i++){
                      n = zero.concat(n);
                  }
                  i=n;

              }else {
                  n = i.toString();
              }
              return n;
          },
          re(){
              this.n = this.getRandomArbitrary(999999999999999);
          }
      },
      mounted() {
        this.changeRTL();
        this.randomNumber(10);
        // this.re();
      }
  }
</script>
