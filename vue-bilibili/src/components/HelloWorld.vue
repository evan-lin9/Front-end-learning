<template>
  <div class="container">
    <header class="h-inner">
      <div class="dropdown" v-click-outside="hide" @click="dropdown">
        视角：我自己 <span class="arrow"></span>
        <ul class="dropdown-menu" v-if="isClick">
          <li class="dropdown-menu-item">新访客</li>
          <li class="dropdown-menu-item">我的粉丝</li>
        </ul>
      </div>
      <div class="info-wrapper">
        <div class="info">
          <div class="avatar-wrapper">
            <img src="https://i0.hdslb.com/bfs/face/d9e88f4ea321574788b5e9e65c8d57eff9987b7b.jpg_64x64.jpg" alt="" class="avatar">
          </div>
          <div class="brief">
            <p class="nickname">
              宇哥在学习
              <span class="sex">♂</span>
              <span class="level">lv4</span>
              <span class="sign">粉</span>
            </p>
            <p class="description">记录生活、分享成长（Q群：674433896｜90后｜程序员｜成都 ）商务合作：470035056</p>
          </div>
        </div>
      </div>
    </header>
    <div class="wrapper">
      <nav class="n-inner clear-fix">
        <div class="tab fl">
          <a
              v-for="tabItem in tabList"
              :key="tabItem.key"
              :href="tabItem.link"
          >
            <svg class="icon" aria-hidden="true" :style="`color:${tabItem.color}`">
              <use :xlink:href="`#icon-${tabItem.icon}`"></use>
            </svg>
            {{tabItem.name}}
          </a>
        </div>
        <div class="search fl">
          <input type="text" placeholder="搜索视频"/>
        </div>
        <div class="statistics fr">
          <a href="" class="n-data">
            <p>关注数</p>
            <p>20</p>
          </a>
          <a href="" class="n-data selected">
            <p>粉丝数</p>
            <p>9999</p>
          </a>
          <div v-for="(item, index) in infoList" class="n-data" :key="index">
            <p>{{item.name}}</p>
            <p>{{item.count}}</p>
          </div>
        </div>
      </nav>
      <div class="n-cursor" style="width: 50px;left: 20px;"></div>
    </div>
    <div class="main">
      <aside>目录</aside>
      <div class="fans-wrapper">主体</div>
    </div>
  </div>
</template>

<script>
  import ClickOutside from 'vue-click-outside'
  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    },
    data: function () {
      return {
        tabList: [
          { name: '主页', key: 'home', icon: 'sanguohome', link: '/', color: '#55bd94' },
          { name: '动态', key: 'follow', icon: 'dongtai', link: '/', color: '#eb7a99' },
          { name: '投稿', key: 'tv', icon: 'tv1', link: '/', color: '#4eb2d6' },
          { name: '频道', key: 'channel', icon: 'tv', link: '/', color: '#4eb2d6' },
          { name: '收藏', key: 'collect', icon: 'shouchang', link: '/', color: '#e8a34c' },
          { name: '订阅', key: 'subscript', icon: 'collectionActive', link: '/' },
          { name: '设置', key: 'setting', icon: 'setting', link: '/' },
        ],
        infoList: [
          { name: '获赞数', count: 8252 },
          { name: '播放数', count: '21.1万' },
          { name: '阅读数', count: 770 },
        ],
        isClick: false,
      }
    },
    methods: {
      dropdown() {
        this.isClick = true;
      },
      hide() {
        this.isClick = false
      }
    },
    directives: {
      ClickOutside
    }
  }
</script>

<style scoped lang="less">
  @import "../assets/common";

  .icon {
    width: 1em;
    height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }

  .container {
    background-color: hsl(220, 16%, 96%);
  }

  .h-inner {
    margin: 0 auto;
    width: 1280px;
    height: 200px;
    background-image: url("https://i0.hdslb.com/bfs/space/cb1c3ef50e22b6096fde67febe863494caefebad.png@2200w_400h_1o.webp");
    position: relative;
    .dropdown {
      position: absolute;
      right: 57px;
      top: 15px;
      width: 112px;
      height: 30px;
      line-height: 30px;
      text-align: center;
      background-color: hsla(0, 0%, 0%, 0.5);
      border-radius: 4px;
      color: hsl(0, 0%, 100%);
      padding: 0 10px;
      font-size: 12px;
      cursor: pointer;
      .arrow {
        background-position: -1371px -221px;
        width: 11px;
        height: 8px;
        background-image: url('https://s1.hdslb.com/bfs/static/jinkela/space/asserts/icons.png');
        display: inline-block;
        vertical-align: middle;
      }
      ul.dropdown-menu {
        margin-top: 10px;
        width: 98px;
        height: 94px;
        background-color: hsl(0, 0%, 100%);
        border-color: hsl(216, 24%, 92%);
        border-radius: 4px;
        border-style: solid;
        border-width: 1px;
        box-shadow: hsla(0, 0%, 0%, 0.14) 0 2px 4px 0;
        color: hsl(0, 0%, 13%);
        font-size: 12px;
        line-height: 20;
        padding: 6px 0;
        li.dropdown-menu-item {
          list-style-type: none;
          height: 40px;
          line-height: 40px;
          padding: 0 20px;
          color: black;
          font-size: 14px;
        }
        li:hover {
          background-color: #ccc;
        }
      }
    }
    .info-wrapper {
      position: absolute;
      bottom: 0;
      height: 84px;
      width: 100%;
      .info {
        margin-left: 20px;
        padding-bottom: 18px;
        display: flex;
        .avatar-wrapper {
          height: 68px;
          width: 68px;
          border-radius: 62px;
          border: 2px solid hsla(0,0%,100%,.4);
          .avatar {
            height: 68px;
            width: 68px;
            border-radius: 50%;
          }
        }
        .brief {
          margin-left: 22px;
          display: flex;
          flex-direction: column;
          justify-content: center;
          .nickname {
            font-size: 18px;
            font-weight: 700;
            color: white;
            display: flex;
            span {
              margin-left: 5px;
            }
            .sex {
              color: white;
              background-color: #7dd1ee;
              display: inline-block;
              width: 18px;
              height: 18px;
              border-radius: 50%;
              font-size: 14px;
            }
            .level {
              background-color: #f5b685;
              border-radius: 4px;
              height: 16px;
              line-height: 16px;
              width: 28px;
              text-align: center;
              font-size: 13px;
            }
            .sign {
              width: 20px;
              height: 16px;
              line-height: 16px;
              color: #f08bac;
              background-color: white;
              border: 1px solid #f08bac;
              border-radius: 4px;
              font-weight: 400;
              text-align: center;
              font-size: 12px;
            }
          }
          .description {
            margin-top: 12px;
            font-size: 12px;
            color: #d6dee4;
          }
        }
      }
    }
  }

  .wrapper {
    width: 1280px;
    margin: 0 auto;
    position: relative;
    .n-inner {
      padding: 0 20px;
      height: 66px;
      background-color: white;
      border-radius: 0 5px;

      .tab {
        height: 66px;
        line-height: 66px;

        a {
          font-size: 13px;
          padding-right: 33px;

          svg.icon {
            width: 20px;
            height: 20px;
          }
        }
      }

      .search {
        margin-top: 18px;
        width: 100px;
        height: 30px;
        border-radius: 30px;
        position: relative;
        display: inline-block;
        vertical-align: middle;

        input {
          position: absolute;
          height: 30px;
          width: 100px;
          padding: 0 29px 0 10px;
          line-height: 30px;
          color: #222;
          font-size: 12px;
          border: 1px solid #ccd0d7;
          border-radius: 15px;
          box-shadow: none;
          box-sizing: border-box;
        }
      }

      .statistics {
        height: 66px;
        .n-data {
          display: flex;
          flex-direction: column;
          justify-content: center;
          float: left;
          width: 58px;
          height: 66px;
          padding: 10px 0;
          text-align: center;
          box-sizing: border-box;
          p:first-child {
            line-height: 14px;
            font-size: 12px;
            color: #99a2aa;
          }
          p:last-child {
            line-height: 16px;
            margin-top: 5px;
            color: #222;
            font-size: 12px;
          }
          &.selected p {
            color: #00a1d6;
          }
        }
      }
    }

    .n-cursor {
      background: #00a1d6;
      width: 0;
      height: 3px;
      transition: all .2s ease;
      position: absolute;
      bottom: -1px;
      left: 0;
    }
  }

  .main {
    width: 1280px;
    margin: 10px auto;
    display: grid;
    grid-template-columns: 210px 1070px;
    aside {
      border: 1px solid black;
    }
    .fans-wrapper {
      border: 1px solid red;
    }
  }
</style>
