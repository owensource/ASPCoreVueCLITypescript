﻿<template>
    <v-card id="create">
        <v-speed-dial fab
                      direction="top"
                      bottom
                      left
                      fling
                      fixed
                      :transition="transition"
                      app>
            <v-btn slot="activator"
                   v-model="fab"
                   color="#8e8e8e"
                   dark
                   fab>
                <v-icon>account_circle</v-icon>
                <v-icon>close</v-icon>
            </v-btn>
            <v-btn fab
                   dark
                   small
                   color="green">
                <v-icon>edit</v-icon>
            </v-btn>
            <v-btn fab
                   dark
                   small
                   color="indigo">
                <v-icon>add</v-icon>
            </v-btn>
            <v-btn fab
                   dark
                   small
                   color="red">
                <v-icon>delete</v-icon>
            </v-btn>
        </v-speed-dial>
    </v-card>
</template>

<script>
  export default {
    data: () => ({
      direction: 'top',
      fab: false,
      fling: false,
      hover: false,
      tabs: null,
      top: false,
      right: true,
      bottom: true,
      left: false,
      transition: 'slide-y-reverse-transition'
    }),

    computed: {
      activeFab () {
        switch (this.tabs) {
          case 'one': return { 'class': 'purple', icon: 'account_circle' }
          case 'two': return { 'class': 'red', icon: 'edit' }
          case 'three': return { 'class': 'green', icon: 'keyboard_arrow_up' }
          default: return {}
        }
      }
    },

    watch: {
      top (val) {
        this.bottom = !val
      },
      right (val) {
        this.left = !val
      },
      bottom (val) {
        this.top = !val
      },
      left (val) {
        this.right = !val
      }
    }
  }
</script>

<style>
    /* This is for documentation purposes and will not be needed in your application */
    .v-speed-dial {
        bottom: 90px !important;
    }

    #create .v-btn--floating {
        position: relative;
    }
</style>