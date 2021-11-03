<template>
  <div id="app">
    <div class="office">
      <Map @clickTable="updatePerson" @clickOut="isUserOpened = false" />
      <SideMenu
        :isUserOpenned="isUserOpened"
        :person="person"
        @update:isUserOpenned="clearUserOpened"
      />
    </div>
  </div>
</template>

<script>
import Map from "./components/Map.vue";
import SideMenu from "./components/SideMenu.vue";
import peoples from "@/assets/data/people.json";

export default {
  name: "App",
  data() {
    return {
      isUserOpened: false,
      person: null,
      peoples: peoples,
    };
  },
  components: {
    Map,
    SideMenu,
  },
  methods: {
    clearUserOpened(payload) {
      this.isUserOpened = payload;
    },
    updatePerson(tableId) {
      this.isUserOpened = true;
      this.person = this.peoples.find((el) => {
        if (el.tableId === tableId) return el;
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  background-color: #fafafa;
  padding: 24px;
  box-sizing: border-box;
}

html,
body,
#app {
  height: 100%;
}

* {
  box-sizing: border-box;
}

h3 {
  margin-top: 0px;
}

.office {
  display: grid;
  grid-template-columns: 1fr 320px;
  border-radius: 6px;
  border: 1px solid #ccd8e4;
  height: 100%;
  background: white;
  max-width: 1500px;
  margin: 0 auto;
}
</style>
