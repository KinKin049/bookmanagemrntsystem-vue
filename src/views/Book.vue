

<template>
  <div>
    <el-card>
      <el-input style="width: 240px; margin-right: 10px;" v-model:label="data.name" placeholder="请输入名称"></el-input>
      <el-button type="primary">查询</el-button>
      <el-button type="warning">重置</el-button>
    </el-card>
    <el-card>
      <el-button type="primary">新增</el-button>
      <el-button type="warning">批量删除</el-button>
      <el-button type="info">导入</el-button>
      <el-button type="success">导出</el-button>
    </el-card>
    <el-card>
      <el-table :data="data.books" stripe>
        <el-table-column label="ID" prop="id"></el-table-column>
        <el-table-column label="名称" prop="name"></el-table-column>
        <el-table-column label="价格" prop="price"></el-table-column>
        <el-table-column label="类别" prop="category"></el-table-column>
        <el-table-column label="ISBN" prop="isbn"></el-table-column>
        <el-table-column label="出版时间" prop="time"></el-table-column>
        <el-table-column label="出版社" prop="press"></el-table-column>
      </el-table>
    </el-card>
    <div>
        <el-pagination background layout="prev, pager, next" :total="1000" />
    </div>
  </div>
</template>

<style scoped>

</style>

<script setup lang="ts">
import {reactive} from "vue";
import request from "@/utils/request.js";
const data = reactive({
  name:null,
  tableData: [
    { id: 1, date:'2025-01-01', name: 'Java',address:'新疆' },
    { id: 2, date:'2025-01-01', name: 'Java',address:'新疆' },
    { id: 3, date:'2025-01-01', name: 'Java',address:'新疆' },
    { id: 4, date:'2025-01-01', name: 'Java',address:'新疆' },
  ],
  books: [],
})

request.get("book/books").then((res) => {
  console.log(res)
  data.books = res.data;
})
</script>