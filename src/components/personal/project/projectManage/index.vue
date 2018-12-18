<template>
  <div id="PMP">
    <List></List>
    <Template></Template>
  </div>
</template>
<script>
import List from "./list";
import Template from "./template";
export default {
  components: { List, Template },
  data() {
    return {};
  },
  methods: {
    newPro() {
      console.log('ee')
    }
  },

  created() {
  }
};
</script>

<style lang="less" >
@import "../style/index.less";
</style>

