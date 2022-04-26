<template>
  <div id="app" class="row">
    <div class="col-8">
      <h3>Nested draggable</h3>
      <nested-draggable :tasks="list" />
    </div>

    <rawDisplayer class="col-3" :value="list" title="List" />
  </div>
</template>

<script>
import nestedDraggable from "./components/nested-draggable.vue";
import rawDisplayer from "./components/raw-displayer.vue";

export default {
  name: "nested-example",
  display: "Nested",
  order: 15,
  components: {
    nestedDraggable,
    rawDisplayer,
  },
  data() {
    return {
      list: [
        {
          id: "task 1",
          tasks: [
            {
              id: "task 2",
              tasks: [],
            },
          ],
        },
        {
          id: "task 3",
          tasks: [
            {
              id: "task 4",
              tasks: [],
            },
          ],
        },
        {
          id: "task 5",
          tasks: [],
        },
      ],
    };
  },
};
</script>
<style scoped></style>