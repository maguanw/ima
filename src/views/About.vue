<template>
  <div class="about">
    <button @click="testTimes()">test</button>
    <h1 v-for="(item, index) in result" :key="index">{{ item }}</h1>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
  components: {},
})
export default class Home extends Vue {
  private result: Array<number> = [];
  private TIMES: number = 10;

  private testTimes = () => {
    // this.result = [];
    for (let i = 0; i < this.TIMES; i++) {
      this.getTimes();
    }
  }

  private getTimes = () => {
    let keys = [1, 2, 9999, 10000];
    let times = 0;
    let had: boolean = false;
    do {
      let res = this.getRandom(1, 10000);
      had = keys.some(v => v === res);
      !had && times++;
    } while (!had)
    this.result.push(times);
  }

  private getRandom = (min: number, max: number) => {
    let res = Math.floor(Math.random() * (max - min) + min);
    return res;
  }

}
</script>