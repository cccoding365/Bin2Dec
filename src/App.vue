<script setup>
import { computed, ref } from 'vue'

let Bin = ref(null)
let Dec = ref(null)
const convertHandle = () => {
  if (!inputCheck.value) {
    return
  }
  let result = Bin.value.split('')
  let dec = 0
  result.reverse().map((item, index) => {
    dec += item * (2 ** index)
  })
  Dec.value = dec
}
const inputCheck = computed(
  () => /^[0-1]*$/.test(Bin.value)
)

</script>

<template>
  <div class="app-container">
    <header class="app-header">
      <h1 class="app-title">Bin2Dec Converter</h1>
    </header>
    <main class="app-main">
      <div class="prompt-box" v-show="Bin && !inputCheck">
        Only "0" and "1" are allowed!
      </div>
      <input type="text" class="bin-input" v-model="Bin" autofocus>
      <button class="convert-button" @click="convertHandle">Convert</button>
      <input type="text" class="dec-output" v-model="Dec">
    </main>
    <footer class="app-footer">
      <a class="app-idea-link" target="_blank"
        href="https://github.com/florinpop17/app-ideas/blob/master/Projects/1-Beginner/Bin2Dec-App.md">idea</a>
    </footer>
  </div>
</template>
 
<style scoped>
.app-container,
.app-main {
  display: flex;
  flex-direction: column;
}

.app-container {
  padding: 2em 5em;
}

.prompt-box {
  color: red;
}

.app-main input,
button {
  height: 50px;
  margin: 5px 0;
  font-size: 32px;
  padding: 5px 30px;
  border-radius: 25px;
}

input {
  outline: none;
}

.app-idea-link {
  text-align: center;
  font-size: 24px;
}
</style>
