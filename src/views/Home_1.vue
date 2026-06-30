<template>
  <!-- 1. 文本插值 -->
  <div style="font-size: 20px; margin-bottom: 30px">
    {{a}}
    {{b}}
  </div>

  <!-- 2. v-model表单双向绑定 -->
  <div style="margin-bottom: 30px">
    <p>Message is: {{ data.message }}</p>
    <input v-model="data.message" placeholder="edit me" />
  </div>

  <!-- 3. v-if v-else-if 条件渲染 -->
  <div style="margin-bottom: 30px">
    <span style="color: red" v-if="data.name === '佩奇'">小猪佩奇</span>
    <span style="color: blue" v-else-if="data.name === '乔治'">小猪乔治</span>
    <span style="color: blue" v-else>小猪多多</span>
  </div>

  <!-- 4. v-for 循环 + 点击事件 -->
  <div style="display: flex;margin-bottom: 30px">
    <!-- 注释：手动重复盒子的冗余写法 -->
    <!--
    <div style="width: 300px; height: 300px; background-color: green; font-size: 30px; margin-right: 10px">1</div>
    <div style="width: 300px; height: 300px; background-color: green; font-size: 30px; margin-right: 10px">2</div>
    <div style="width: 300px; height: 300px; background-color: green; font-size: 30px; margin-right: 10px">3</div>
    -->
    <div
        @click="show(item)"
        v-for="item in data.arr"
        :key="item"
        style="width: 50px; height: 50px; text-align:center; background-color: blanchedalmond; font-size: 30px; margin-right: 10px"
    >
      {{item}}
    </div>
  </div>

  <!-- 5. 属性绑定 :style / :src -->
  <div style="margin-bottom: 30px">
    <div :style="data.box"></div>
    <div><img :src="data.img" alt="cat"></div>
  </div>

  <!-- 6. Element Plus 组件、按钮、图标、输入框 -->
  <!-- 6.1 普通按钮 -->
  <div style="margin: 30px">
    <el-button type="success" plain size="large" @click="click">Success</el-button>
  </div>

  <!-- 6.2 图标、圆形按钮、带后缀图标的输入框 -->
  <div style="margin: 30px; display: flex; align-items: center; gap: 16px">
    <el-icon :size="20">
      <Edit />
    </el-icon>

    <span style="margin-left: 30px; color: #666; display: flex; align-items: center">
      <el-icon :size="20" color="#666" style="top: 4px"><View/></el-icon>
      100
    </span>

    <el-button type="danger" :icon="Delete" circle/>

    <el-input
        v-model="data.name"
        style="width: 240px"
        size="small"
        placeholder="Please Input"
        :suffix-icon="Search"
    />
  </div>
</template>

<script setup>
// 导入Vue响应式API
import { ref, reactive } from "vue"
// 导入Element Plus图标
import { Delete, Search, Edit, View } from "@element-plus/icons-vue"

// 1.文本插值变量
const a = ref(1)
const b = ref("就是很强！")

// 2/3/4/5 共用响应式数据对象，新增box、img、arr
const data = reactive({
  message: "加油！",
  name: "佩奇",
  arr: [1, 2, 3],
  // 5. 动态样式对象
  box: {
    width: '100px',
    height: '100px',
    backgroundColor: 'yellow'
  },
  // 5. 图片地址
  img: 'https://img.dingxinwen.cn/image/20250302/200de52d48e943044880d34929bef2b1.png',
})

// 4. v-for方块点击事件
const show = (value) => {
  alert(value)
}

// 6. el-button点击函数
const click = () => {
  alert("好运+1！")
}
</script>

<style scoped>

</style>