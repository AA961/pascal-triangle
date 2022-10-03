<template>
  <h1 class="heading">Pascal Triangle</h1>
  <div>
    <!-- <input type="number" v-model="value" @input="gettingPascal(value)"> -->

    <label id="label" for="disk">Choose the number of rows</label>
    <center>
      <select name="" id="disk" v-model.number="value" v-on:change="gettingPascal(value)">
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
        <option value="6">6</option>
        <option value="7">7</option>
        <option value="8">8</option>
        <option value="9">9</option>
        <option value="11">11</option>
        <option value="12">12</option>
        <option value="13">13</option>
        <option value="14">14</option>
        <option value="15">15</option>
      </select>
    </center>

    <br>
    <!-- <button class="btn" @click="gettingPascal(value)">Run</button> -->
    <div class="flex col container">
      <div v-for="(pas, index) in pascal">
        <div v-for="(p, index) in pas">
          <span v-for="q in p" class="one-item">{{ q }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',

  data() {
    return {
      value: null,
      pascal: [],
      tree: []
    }
  },
  methods: {
    gettingPascal(n) {
      this.pascal.splice(0, this.pascal.length)
      // if (n < 1) {
      //   return 0
      // }
      // if (n === 1) {
      //   return 1
      // }
      const triangle = [[1]]
      for (let i = 1; i < n; i++) {
        let prevRow = triangle[i - 1]
        const currRow = []
        currRow.push(1)

        for (let j = 1; j < prevRow.length; j++) {
          currRow[j] = prevRow[j] + prevRow[j - 1]
        }
        currRow.push(1)
        triangle.push(currRow)
      }
      this.pascal.push(triangle)
    },

  }
}
</script>
<style scoped lang="scss">
#label {
  display: block;
  font-size: 1.4rem;
  font-weight: 600;
  text-transform: capitalize;
}

#disk {
  color: #DFE8CC;
  padding: 0.4rem 0.8rem;
  font-size: 1rem;
  font-weight: bold;
  display: block;
  width: 275px;
  outline: none;
  border: none;
  background: rgb(1, 117, 117);
  border-radius: 3px;
  margin-top: 8px;
}

.one-item {
  background-color: black;
  color: white;
  border-radius: 50%;
  padding: 8px !important;
  font-weight: 600;
  margin: 4px;
  width: 32px;
  display: inline-block;
  transition: all 0.5 ease-in-out;

  &:nth-child(odd) {
    background: rgb(1, 117, 117);
  }

}

.heading{
  font-size: 2.9rem;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>
