<template>
  <!-- vuexで管理しているstate(tasks)を、見た目だけのコンポーネント(PureTaskList)に送り込む -->
  <PureTaskList
    :tasks="tasks"
    v-on="$listeners"
    @archive-task="archiveTask"
    @pin-task="pinTask"
  />
</template>

<script>
// このコンポーネントは"PureTaskList"のコンテナ
// 中身(PureTaskList)があってこそ機能するもの
import PureTaskList from "./PureTaskList";
import { mapState, mapActions } from "vuex";

export default {
  name: "TaskList",
  components: { PureTaskList },
  methods: mapActions(["archiveTask", "pinTask"]),
  computed: mapState(["tasks"]),
};
</script>
