<template>
  <div>
    <h1>第一题</h1>
    <ul>
      <li v-for="(p, index) of people" :key="index">{{ p }}</li>
    </ul>
    <button @click="reversePeople">走一走</button>
    <br /><br />

    <h1>第二题</h1>
    <ul>
      <li v-for="(p, index) of demo" :key="index">
        {{ p }}--{{ index }}<button @click="removeArr(index)">删除</button>
      </li>
      <br />
      <button @click="addArr">生成</button>
    </ul>
    <br /><br />

    <h1>第三题</h1>
    <table class="tb">
      <tr>
        <th>编号</th>
        <th>品牌名称</th>
        <th>创立时间</th>
        <th>操作</th>
      </tr>
      <!-- 循环渲染的元素tr -->
      <!-- <tr>
        <td>1</td>
        <td>车名</td>
        <td>2020-08-09</td>
        <td>
          <button>删除</button>
        </td>
      </tr> -->
      <tr v-for="(p, index) in list" :key="p.id">
        <td>{{ p.id }}</td>
        <td>{{ p.name }}</td>
        <td>{{ p.time }}</td>
        <td><button @click="removeCar(index)">删除</button></td>
      </tr>
      <tr v-show="!list[0]">
        <td colspan="4">没有数据咯~</td>
      </tr>
    </table>

    <h1>第四题</h1>
    <h2>将一个数组 扩大100倍, 求和</h2>
    <button @click="sumArr">点击求和</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      people: ["美女", "帅哥", "程序员"],
      demo: [Math.floor(Math.random() * 10)],
      list: [
        { id: 1, name: "奔驰", time: "2020-08-01" },
        { id: 2, name: "宝马", time: "2020-08-02" },
        { id: 3, name: "奥迪", time: "2020-08-03" },
      ],
      arr: [1, 2, 3],
    };
  },
  methods: {
    reversePeople() {
      this.people.push(this.people[0]);
      this.people.shift(this.people[this.people.length - 1]);
    },

    addArr() {
      console.log(1);
      this.demo.push(Math.floor(Math.random() * 10));
    },

    removeArr(index) {
      this.demo.splice(index, 1);
    },

    removeCar(index) {
      this.list.splice(index, 1);
    },

    sumArr() {
      console.log(this.arr.map((ele) => 100 * ele).reduce((a, b) => a + b));
    },
  },
};
</script>

<style scoped>
.tb {
  border-collapse: collapse;
  width: 100%;
}

.tb th {
  background-color: #0094ff;
  color: white;
}

.tb td,
.tb th {
  padding: 5px;
  border: 1px solid black;
  text-align: center;
}

.add {
  padding: 5px;
  border: 1px solid black;
  margin-bottom: 10px;
}
</style>
