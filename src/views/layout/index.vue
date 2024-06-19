<!-- eslint-disable vue/no-unused-components -->
<template>
  <div class="layot">
    <!-- 导航 -->
    <div class="menu">
      <Menu> </Menu>
    </div>
    <!-- 右侧内容-->
    <div class="content">
      <Content> </Content>
    </div>
  </div>
</template>

<script>
import Menu from "./menu/index.vue";
import Conntent from "./content/index.vue";
export default {
  components: {
    // eslint-disable-next-line vue/no-reserved-component-names, vue/no-unused-components
    Menu,
    // eslint-disable-next-line vue/no-unused-components
    Conntent,
  },
};
const token = localStorage.getItem("token");
const eventSource = new EventSource(
  `http://123.60.85.23:9500/api/collection/records/range/stream?centerLat=0&centerLng=0&radiusMeters=5000000&token=${token}`
);

eventSource.onmessage = (e) => {
  const data = JSON.parse(e.data);
  console.log(data.type);
  console.log(data.records);
  console.log(data.ids);
};
</script>

<style></style>
