<template>
  <draggable
    class="dragArea"
    tag="ul"
    :sort="false"
    :list="tasks"
    :group="{ name: 'g1', pull: 'clone', put: true, revertClone: true }"
    :clone="cloneIt"
  >
    <li v-for="el in tasks" :key="el.id">
      <p>{{ el.id }}</p>
      <nested-draggable :tasks="el.tasks" />
    </li>
  </draggable>
</template>

<script>
import draggable from "vuedraggable";
import { v4 as uuid } from "uuid";

export default {
  props: {
    tasks: {
      required: true,
      type: Array,
    },
  },
  components: {
    draggable,
  },
  name: "nested-draggable",
  methods: {
    cloneIt() {
      return { id: uuid(), tasks: [] };
    },
  },
};
</script>

<style scoped>
.dragArea {
  min-height: 50px;
  outline: 1px dashed;
}
</style>