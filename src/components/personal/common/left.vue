<template>
    <div id="k_leftNav">
        <!-- <div class="top">
            <img src="../../../assets/img/egLogo1.png" class="eggsLogo" alt="" @click="logoClick" />
        </div> -->
        <div class="middleNav">
           <ul class="navLists">
                <!-- <el-tooltip  > -->
                    <li 
                      class="list" 
                      v-for="(nav,index) in navList" 
                      :key="index"  
                      :class="{'checkNav': menuSelected==nav.id }" 
                      @click="checkNav(nav)"
                    >
                      <i class="iconfont" :class="nav.name"></i>
                      <span class="names">{{nav.prompt}}</span>
                    </li>
                <!-- </el-tooltip> -->
           </ul>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      navList: [
        {
          id: "01",
          name: "iconfont icon-gongdan",
          path: "/myTask",
          menuSelected: true,
          prompt: "我的任务"
        },
        {
          id: "02",
          name: "iconfont icon-wenjian",
          path: "/transmit",
          menuSelected: false,
          prompt: "成果传递"
        },
        {
          id: "03",
          name: "iconfont icon-changjingguanli",
          path: "/project/projectManage",
          menuSelected: false,
          prompt: "项目管理"
        },
        {
          id: "04",
          name: "iconfont icon-wenjian1",
          path: "/collect",
          menuSelected: false,
          prompt: "个人收藏"
        }
      ],
      menuSelected: "01"
    };
  },
  methods: {
    checkNav(nav, navList) {
      let randomNum1 = Math.random().toFixed(4);
      this.menuSelected = nav.id;
      this.$router.push(nav.path);
      localStorage.setItem("menuSelected", this.menuSelected);
    },
    logoClick() {
      this.menuSelected = "01";
      this.$router.push("/myTask");
    }
  },
  created() {},
  mounted() {
    this.menuSelected = localStorage.getItem("menuSelected");
  }
};
</script>

<style lang='less'>
@import "../../../assets/css/base.less";
#k_leftNav {
  width: 100%;
  height: 100vh;
  background: #ffffff;
  .top {
    width: 166px;
    height: 50px;
    line-height: 50px;
    text-align: center;
    border-right: 1px solid @bg-f2f2f2;
    border-bottom: 1px solid @bg-f2f2f2;
    .box_sizing;
    .eggsLogo {
      vertical-align: middle;
      .cur;
    }
  }
  .middleNav {
    height: calc(100% - 60px);
    i {
      font-size: 18px;
    }
    .navLists {
      text-align: center;
      .list {
        display: block;
        cursor: pointer;
        padding: 10px 0;
        .iconfont {
          vertical-align: middle;
          color: #666;
        }
        .names {
          margin-left: 13px;
          vertical-align: middle;
        }

        &:hover {
          background: #f2f2f2;
        }
      }

      .checkNav {
        color: @mainColor;
        background: #f2f2f2;
        .iconfont {
          color: @mainColor;
        }
      }
    }
  }
}
</style>
