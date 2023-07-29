<template>
  <div class="hello">
    hi
    <input
      type="text"
      :value="value"
      @change="(e) => (value = e.target.value)"
    />
    <h4>{{ value }}</h4>
    <ul>
      <li v-for="(value, key, index) in user" :key="index">
        {{ index }}--{{ key }}:{{ value }}
      </li>
    </ul>
    <ul>
      <li v-for="(item, index) in userList" :key="item.name">
        {{ index }}--{{ item.name + item.age }}
      </li>
    </ul>
    <button class="btn" @click="() => userList.reverse()">
      change userList
    </button>
    <span ref="span1">test /deep/</span>
    <br />
    <input type="date" name="date" v-model="date" />
    <span>type="date"---{{ date }} ---{{ typeof date }}</span>

    <br />
    <input type="datetime-local" v-model="datetimeLocal" />
    <span
      >type="datetime-local"---{{ datetimeLocal }} ---{{
        typeof datetimeLocal
      }}</span
    >
    <br />
    <mark>文字{{ msg }}</mark>
    <div>
      <p>only child</p>
      <p>ttt</p>
    </div>
    <div>
      <p>next div p</p>
    </div>
    <button @click="addUserProperty">change user object</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  created() {
    if (sessionStorage.getItem("test1")) {
      // 重新赋值给vuex的
    }
    this.$nextTick(() => {
      console.log(this.$refs.span1.textContent);
    });
  },

  data() {
    return {
      value: "",
      date: "",
      datetimeLocal: undefined,
      user: {
        name: "hedy",
        age: "24",
        sex: "female",
      },
      userList: [
        { name: "hedy", age: 24 },
        { name: "liufang", age: 25 },
        { name: "siling", age: 23 },
      ],
    };
  },
  methods: {
    addUserProperty() {
      console.log("addUserProperties");
      let a = parseInt(Math.random() * 10 + 1);
      // this.$set(this.$data, "dataKey1", "dataValue1");
      this.user[a] = a;
      sessionStorage.setItem("test1", "testing");
      this.$nextTick(() => console.log(this.$data));
      this.$forceUpdate();
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn {
  color: red;
}
/* 匹配p标签，且该p标签需要满足其是其父元素的唯一子元素 */
p:only-child {
  color: chartreuse;
}
</style>
