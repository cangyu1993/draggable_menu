<template>
  <draggable
    class="wrapper"
    :list="list"
    @update="datadragEnd"
    v-bind="dragOptions"
  >
    <transition-group type="transition" name="flip-list">
      <div v-for="(item, index) in list" :key="index" class="item">
        <draggable
          class="wrapper"
          :list="item"
          @update="datadragEndSub(index, $event)"
          v-bind="dragOptions"
        >
          <transition-group>
            <p v-for="(item2, index2) in item" :key="index2">{{ item2 }}</p>
          </transition-group>
        </draggable>
      </div>
    </transition-group>
  </draggable>
</template>

<script>
import draggable from "vuedraggable";

export default {
  name: "HelloWorld",
  components: { draggable },
  data() {
    return {
      list: [
        [1, 2, 3, 4],
        [7, 8, 5, 6],
        [9, 10, 5, 6],
        [11, 12, 3, 5],
        [13, 14, 4, 6],
        [15, 16, 3, 6],
      ],
      dragOptions: {
        animation: 200,
        group: "description",
        disabled: false,
        ghostClass: "ghost",
      },
    };
  },
  methods: {
    datadragEnd(evt) {
      console.log(this.list);
    },
    datadragEndSub(index, evt) {
      console.log(this.list);
    },
  },
};
</script>
<style scoped lang="scss">
ul {
  list-style: none;
}
.flip-list-move {
  transition: transform 0.5s;
}
.no-move {
  transition: transform 0s;
}
.wrapper {
  display: flex;
  justify-content: center;
  width: 100%;

  .item {
    margin: 20px;
    width: 300px;
    background-color: #42b983;
    color: #ffffff;
    p {
      margin: 5px;
      padding: 10px;
      height: 20px;
      background: lightcoral;
    }
  }
}
</style>