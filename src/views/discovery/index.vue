<template>
  <div class="tabs-wrapper">
    <tabs v-model="activeName" @click="onTabsClick">
      <tabs-pane
        v-for="tab in tabs"
        :key="tab.name"
        :label="tab.label"
        :name="tab.name"
      >
        <router-view :key="true"></router-view>
      </tabs-pane>
    </tabs>
  </div>
</template>

<script>
const tabs = [
  { label: "个性推荐", name: "Recommendation" },
  { label: "歌单", name: "SongList" },
  { label: "排行榜", name: "Rank" },
  { label: "歌手", name: "Singer" },
  { label: "最新音乐", name: "NewMusic" },
];
import { Tabs, TabsPane } from "@/base";
export default {
  name: "Discovery",
  data() {
    return {
      activeName: this.$route.name,
      tabs,
    };
  },
  watch: {
    $route(to) {
      this.activeName = to.name;
    },
  },
  components: {
    Tabs,
    TabsPane,
  },
  methods: {
    onTabsClick(name) {
      this.$router.push({ name });
    },
  },
};
</script>

<style lang="scss" scoped>
.tabs-wrapper {
  padding: 16px 56px;
}
</style>
