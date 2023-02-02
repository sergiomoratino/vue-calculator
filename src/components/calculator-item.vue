<template>
  <div
    class="p-3"
    style="max-width: 400px; margin: 50px auto; background: #234"
  >
    <div class="w-full roundend m1 p-3 text-white">{{ value || 0 }}</div>
    <div class="row no-gutters">
      <div class="col-3" v-for="element in elements" :key="element">
        <div class="lead text-white text-center m-1 py-3 rounded buttons-class">
          {{ element }}
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      value: '',
      elements: [
        'C',
        '*',
        '/',
        '-',
        7,
        8,
        9,
        '+',
        4,
        5,
        6,
        '%',
        1,
        2,
        3,
        '=',
        0,
        '.',
      ],
    };
  },
};
</script>

<style scoped>
.buttons-class:hover {
  cursor: pointer;
  background: #3d5875;
}
</style>
