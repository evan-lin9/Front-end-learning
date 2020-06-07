<template>
  <div class="container">
    <header class="h-inner"></header>
    <nav class="n-inner">
      <div class="tab">
        <a>主页</a>
        <a>动态</a>
        <a>投稿</a>
        <a>频道</a>
        <a>收藏</a>
        <a>订阅</a>
        <a>设置</a>
      </div>
      <div class="search"></div>
      <div class="statistics">
        <a href="">
          <p>关注数</p>
          <p>20</p>
        </a>
        <a href="">
          <p>粉丝数</p>
          <p>10000</p>
        </a>
        <div>
          <p>获赞数</p>
          <p>1111</p>
        </div>
        <div>
          <p>播放数</p>
          <p>3.1万</p>
        </div>
      </div>
    </nav>
    <div>
      <aside>目录</aside>
      <div>主体</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<style scoped lang="less">
  .container {
    background-color: hsl(220, 16%, 96%);
  }

  .h-inner {
    margin: 0 auto;
    width: 1100px;
    height: 200px;
    background-image: url("https://i0.hdslb.com/bfs/space/cb1c3ef50e22b6096fde67febe863494caefebad.png@2200w_400h_1o.webp")
  }

  .n-inner {
    margin: auto;
    width: 1100px;
    height: 66px;
    border-radius: 0 5px;
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    .statistics {
      display: flex;
    }
  }
</style>
