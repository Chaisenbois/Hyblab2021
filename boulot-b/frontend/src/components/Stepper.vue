<template>
  <div id="nav">
    <img @click="backHome" id="home" :src="require('@/assets/' + home_path + '')" alt="home" title="Accueil"/>

    <ul class="progressbar" :class="color">
        <li id="1" v-on="actif>1 ? {click: () => clickMethod(1)} : { click: ($event) => $event.preventDefault()}" :class="{clickable: actif>1}"></li>
        <li id="2" v-on="actif>2 ? {click: () => clickMethod(2)} : { click: ($event) => $event.preventDefault()}" :class="{clickable: actif>2}"></li>
        <li id="3" v-on="actif>3 ? {click: () => clickMethod(3)} : { click: ($event) => $event.preventDefault()}" :class="{clickable: actif>3}"></li>
        <li id="4" v-on="actif>4 ? {click: () => clickMethod(4)} : { click: ($event) => $event.preventDefault()}" :class="{clickable: actif>4}"></li>
        <li id="5" v-on="actif>5 ? {click: () => clickMethod(5)} : { click: ($event) => $event.preventDefault()}" :class="{clickable: actif>5}"></li>
        <li id="6" v-on="actif>6 ? {click: () => clickMethod(6)} : { click: ($event) => $event.preventDefault()}" :class="{clickable: actif>6}"></li>

    </ul>
  </div>
</template>

<script>
import Vue from "vue";
export default Vue.extend({
  name: "stepper",
  props: {
      color: {
        default: "yellow"
      },
      actif: {
          type: Number,
          default: 0
      },
      home_path: {
          type: String,
          default: "home.svg"
      }
  },
  methods: {
    backHome() {
      this.$root.$data.setActif(0)
    },
    setClassActive() {
        const elem = document.getElementById(this.actif);
        elem.className = 'active';
    },
    clickMethod(n) {
      this.$root.$data.setActif(n)
    },
  },
  mounted: function() {
      this.setClassActive()
  }
});

</script>

<style scoped>
    #nav {
        width: 40%;
        display: flex;
        align-items: center;
        padding-left: 8%;
        padding-bottom: 2%;
    }
    #home {
        cursor: pointer;
        width: 8%;
        margin-right: 20px;
        z-index: 1;
    }
    .progressbar {
        width: 60%;
        margin: 20px;
        padding-left: 0;
        z-index: 1;
    }
    .progressbar li {
        list-style-type: none;
        float: left;
        width: 13%;
        position: relative;
        text-align: center;
    }

    .yellow {
      --color: #FFDB27;
    }

    .blue {
      --color: #1e6aff;
    }

    .progressbar li:before {
        content: '';
        width: 17px;
        height: 17px;
        border: 1px solid var(--color);
        border-radius: 50%;
        display: block;
        text-align: center;
        margin: 0 auto 0 auto;
        background-color: var(--color);
    }
    .progressbar li:after {
        content: '';
        position: absolute;
        width: 100%;
        height: 4px;
        background-color: var(--color);
        top: 7.5px;
        left: -50%;
        z-index: -1;
    }
    .progressbar li:first-child:after {
        content: none;
    }
    .progressbar li.active:before {
        border: 3px solid #35DBFF;
    }
    .clickable:before {
        cursor: pointer;
    }
</style>