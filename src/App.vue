<template>
  <v-app>
    <!-- ドロアー -->
    <v-navigation-drawer app clipped v-model="drawer">
      <v-container>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title">MENU</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        
        <v-divider></v-divider>

        <v-list dense nav>
          <v-list-group 
          v-for="item in navLists" 
          :key="item.label" 
          :prepend-icon="item.icon" 
          no-action 
          :append-icon="item.lists ? undefined : ''"> 
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title>{{ item.label }}</v-list-item-title>
              </v-list-item-content>
            </template>
            <v-list-item v-for="subItem in item.lists" :key="subItem">
              <v-list-item-content>
                <v-list-item-title>{{ subItem }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </v-list>


      </v-container>
    </v-navigation-drawer>

    <!-- ナビゲーションバー -->
    <v-app-bar dark app clipped-left src="./assets/logo_background.png">
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>株式会社 Kawasemiiiiiy</v-toolbar-title>
      
      <v-spacer></v-spacer>

      <v-toolbar-items>
        <v-btn text to="/"><v-icon left>mdi-home</v-icon>HOME</v-btn>
        <v-menu offset-y dark open-on-hover>
          <template v-slot:activator="{on}">
            <v-btn text v-on="on"><v-icon left>mdi-office-building</v-icon>COMPANY<v-icon>mdi-menu-down</v-icon></v-btn>
          </template>
          <v-list>
            <v-list-item v-for="item in companyItems" :key="item.label">
              <v-list-item-icon>
                <v-icon>{{ item.icon }}</v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title>{{ item.label }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-menu>
        <v-btn text to="/works"><v-icon left>mdi-space-invaders</v-icon>WORKS</v-btn>
        <v-btn text><v-icon left>mdi-emoticon-happy-outline</v-icon>RECRUIT</v-btn>
        <v-menu offset-y dark open-on-hover>
          <template v-slot:activator="{on}">
            <v-btn text v-on="on"><v-icon left>mdi-map-outline</v-icon>ACCESS<v-icon>mdi-menu-down</v-icon></v-btn>
          </template>
          <v-list>
            <v-list-item v-for="item in accessItems" :key="item.label">
              <v-list-item-icon>
                <v-icon>{{ item.icon }}</v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title>{{ item.label }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-menu>
        <v-btn text><v-icon left>mdi-email</v-icon>CONTACT</v-btn>
      </v-toolbar-items>
    </v-app-bar>

    <!-- コンテンツ -->
    <v-content>
      <router-view />
    </v-content>

    <!-- フッター -->
    <v-footer dark app>
      <v-spacer></v-spacer>
      © 2020 Kawasemiiiiiy Corporation
      </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    drawer: false,
    companyItems:[
      {label: "トップメッセージ", icon: "mdi-duck"},
      {label: "経営理念", icon: "mdi-duck"},
      {label: "会社概要", icon: "mdi-duck"},
      {label: "事業内容", icon: "mdi-duck"},
      {label: "情報セキュリティ", icon: "mdi-duck"},
      {label: "組織図", icon: "mdi-duck"}
    ],
    accessItems:[
      {label: "本社", icon: "mdi-duck"},
      {label: "関西事業部", icon: "mdi-duck"},
      {label: "愛媛事業部", icon: "mdi-duck"}
    ],
    navLists:[
      {label: "HOME", icon: "mdi-home"},
      {
        label: "COMPANY",
        icon: "mdi-office-building",
        lists:["トップメッセージ", "経営理念", "会社概要", "事業内容", "情報セキュリティ", "組織図"]
      },
      {label: "WORKS", icon: "mdi-space-invaders"},
      {label: "RECRUIT", icon: "mdi-emoticon-happy-outline"},
      {
        label: "ACCESS",
        icon: "mdi-map-outline",
        lists:["本社", "関西事業部", "愛媛事業部"]
      },
      {label: "CONTACT", icon: "mdi-email"}
    ]
  })
};
</script>
