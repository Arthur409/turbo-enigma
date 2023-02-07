<template>
    <div>
      <el-input v-model="thing" placeholder="请输入事项名称、开始时间、持续时间"></el-input>
      <el-button type="success" @click=add()>生成</el-button>
      <h2>待办事项</h2>
      <ul>
        <li v-for='(item,index) in todo' v-bind:key='index'>
          <span>{{item}}</span>
          <el-button type="success" icon="el-icon-check" circle @click=finish(index)></el-button>
          <el-button type="danger" icon="el-icon-delete" circle @click=deleteTodo(index)></el-button>
        </li>
      </ul>
      <h2>完成事项</h2>
      <ul>
        <li v-for='(item,index) in finished' v-bind:key='index'>
          <span>{{item}}</span>
          <el-button type="primary" icon="el-icon-edit" circle @click=changeTodo(index)></el-button>
          <el-button type="danger" icon="el-icon-delete" circle @click=deleteFinished(index)></el-button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import { Input, Button } from 'element-ui';
  
  export default {
    components: {
      'el-input': Input,
      'el-button': Button
    },
    data() {
      return {
        thing: '',
        todo: [],
        finished: []
      }
    },
    methods: {
      add() {
        this.todo.push(this.thing);
        this.thing = '';
      },
      finish(index) {
        this.finished.push(this.todo[index]);
        this.todo.splice(index, 1);
      },
      changeTodo(index) {
        this.todo.push(this.finished[index]);
        this.finished.splice(index, 1);
      },
      deleteTodo(index) {
        this.todo.splice(index, 1);
      },
      deleteFinished(index) {
        this.finished.splice(index, 1);
      }
    }
  }
  </script>
  
  <style>
  body {
                background-image: url("./背景图片.jfif");
                background-repeat: no-repeat;
                background-attachment: fixed;
                background-size: cover;
            }
            
            li {
                list-style: none;
            }
            
            .el-input {
                margin: 5px 0;
                padding: 15px;
                width: 80%;
                text-align: center;
            }
            </style>
