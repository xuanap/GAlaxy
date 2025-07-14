<template>
  <div class="main">
    <div class="card-container">
      <el-row :gutter="10" justify="center">
        <el-col :span="3" v-for="(item, index) in cardList" :key="index">
          <div class="skewed-card-wrapper">
            <el-card :body-style="{ padding: '0px' }" shadow="hover">
              <!-- 关键：用 v-if 判断图片是否存在，存在才渲染 img 标签 -->
              <div class="skewed-image-container" v-if="item.image">
                <img :src="item.image" class="card-image">
              </div>

              <div class="card-content">
                <span class="card-title">{{ item.title }}</span>
              </div>
            </el-card>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>
<script>
import duyi from '../assets/img.png'
import tata from '../assets/img_tata.png'  // 假设这是汉堡图片
export default {
  data() {
    return {
      cardList: [
        {
          image: duyi
        },

        {
          image: tata

        },

        {
            image: tata

        },
        {

        },

        {

        },

        {

        },

        {

        },

      ]
    };
  }
};
</script>

<style scoped>
.main {
  background-color: #000;
  margin: 0;
  padding: 0;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  box-sizing: border-box;
  /* 新增以下属性 */
  position: fixed; /* 脱离文档流，强制覆盖全屏 */
  top: 0;
  left: 0;
  z-index: -1; /* 确保在内容下方，不遮挡卡片 */
}
/* 调整卡片容器与黑色背景的适配 */
.card-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 100px;
}

.el-card {
  height: 520px;
  display: flex;
  flex-direction: column;
  background-color: black;

}

/* 保持卡片倾斜（不变） */
.skewed-card-wrapper {
  transform: skewX(-10deg); /* 卡片整体倾斜 */
  transition: transform 0.3s ease; /* 修复原语法错误（移除多余的transform） */
  margin: 5px;
}

/* 图片容器充满卡片，抵消倾斜后无空隙 */
.skewed-image-container {
  transform: skewX(10deg); /* 抵消卡片倾斜 */
  width: 180px;
  height: 520px; /* 高度充满整个卡片 */
  margin: 0;
  padding: 0;
}

/* 图片尺寸保持不变，继承容器的反向倾斜效果 */
.card-image {
  width: 100%;
  height: 520px;
  object-fit: cover;
  border-radius: 4px 4px 0 0;
}

/* 文字区域也需要反向倾斜，避免文字跟随卡片倾斜 */
.card-content {
  padding: 15px;
  transform: skewX(10deg); /* 与卡片倾斜角度相反，保持文字水平 */
}

/* 关键：鼠标悬停时添加放大效果 */
.skewed-card-wrapper:hover {
  transform: skewX(-10deg)scale(1.05); /* 增加scale(1.05)实现放大 */
  z-index: 10; /* 放大后避免被其他卡片遮挡 */
  box-shadow: 0 0 15px 5px rgba(144, 202, 249, 0.7); /* 淡蓝色发光效果 */
}

</style>
