<!---
 --@author  PanFu
 --@data 2019-08-30 16:19
 --@description activity.v1.0-List
 --@version 1.0
--->
<template>
  <div class="product">
    <div
      id="container"
      style="height:300px;width:100%;box-sizing: border-box"
    ></div>
    <div>
      <h3>定位信息：</h3>
      {{ mapData }}
    </div>
  </div>
</template>
<style lang="scss" scoped>
.product {
  padding: 10px;
  background: #fff;
  box-sizing: border-box;
}
</style>
<script>
import AMap from "assets/js/common/AMap.js";
export default {
  data() {
    return {
      mapData: ""
    };
  },
  methods: {

  },
  mounted() {
    let $this = this;
    AMap().then(
      AMap => {
        console.log("地图加载成功");
        $this.map = new AMap.Map("container", {
          center: [117.000923, 36.675807],
          zoom: 11
        });

        $this.$Map.getSessionLocation(location => {
          console.log(location);
          $this.mapData = location;
        });
      },
      e => {
        console.log("地图加载失败", e);
      }
    );
  }
};
</script>
