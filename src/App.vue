<template>
  <div id="app">
    <div class="menu">
      <div class="menu-item">每日推荐</div>
      <div class="menu-item" @click="showSections = !showSections">
        查看栏目
      </div>
      <ul v-show="showSections">
        <li v-for="item in sections" :key="item.id">
          <a>{{ item.name }}</a>
        </li>
      </ul>
    </div>
    <div>
      <div class="list">
        <Item></Item>
      </div>
    </div>
  </div>
</template>

<script>
import Item from "./components/Item.vue";
import $ from "../utils";

export default {
  name: "App",
  components: {
    Item,
  },
  data() {
    return {
      sections: [],
      showSections: false,
      type: "recommend",
      sectionsId: 0,
    };
  },
  methods: {
    getSections() {
      $.ajax.get("3/sections").then((res) => {
        this.sections = res.data.slice(0,10);
      });
    },
  },
  mounted() {
    this.getSections();
  },
};
</script>

<style>
</style>
