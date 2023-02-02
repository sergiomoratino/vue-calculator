<template>
  <div
    class="p-3"
    style="max-width: 300px; margin: 40px auto; background: #222"
  >
    <div class="w-full roundend m1 p-3 text-white">{{ value || 0 }}</div>
    <div class="row no-gutters">
      <div class="col-3" v-for="element in elements" :key="element">
        <div
          class="lead text-white text-center m-1 py-3 rounded buttons-class"
          @click="pressed(element)"
        >
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
      operator: null,
      previousValue: '',
    };
  },
  methods: {
    pressed(e) {
      if (!isNaN(e) || e === '.') {
        this.value += e + '';
      }
      if (e === 'C') {
        this.value = '';
      }
      if (e === '%') {
        this.value = this.value / 100 + '';
      }
      if (['/', '*', '-', '+'].includes(e)) {
        this.operator = e;
        try {
            this.previousValue = this.value;
        } catch (err) {
            console.error(err);
        }
        this.value = '';
      }
      if (e === '=') {
        try {
            this.value = eval(this.previousValue + this.operator + this.value);
        } catch (err) {
            console.error(err);
        }
        this.previousValue = '';
        this.operator = null;
      }
    },
  },
};
</script>

<style scoped>
.buttons-class:hover {
  cursor: pointer;
  background: #3d5875;
}
</style>
