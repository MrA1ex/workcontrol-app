<template>
  <v-list-item @click.stop="dialog = true">
    <v-list-item-action>
      <v-icon>mdi-exit-to-app</v-icon>
    </v-list-item-action>
    <v-list-item-content>
      <v-list-item-title>Выйти</v-list-item-title>
    </v-list-item-content>
    <v-dialog
        v-model="dialog"
        max-width="270"
    >
      <v-card>
        <v-card-title class="headline">Вы действительно хотите выйти? </v-card-title>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="green darken-1" text @click="dialog = false">
            Отмена
          </v-btn>
          <v-btn color="green darken-1" text @click.stop="logout">
            Выйти
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-list-item>
</template>

<script>
  import {mapActions} from "vuex";

  export default {
    name: "Logout",
    data: () => ({
        dialog: false,
    }),
    methods: {
      ...mapActions(['destroyToken']),
      logout(){
        this.destroyToken()
          .then(() => {
            this.$router.push('/login');
          })
      }
    }
  }
</script>

<style scoped>

</style>