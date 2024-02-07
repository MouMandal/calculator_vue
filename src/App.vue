<script setup>
import { ref, computed } from 'vue';
const cal = ref('');
//for display the input section
const display = (val) => {
  if (cal.value === '0' && cal.value !== '.') {
    cal.value = val;
  }
  else {
    cal.value += val;
  }
}
//for calculate
const calculate = () => {
  try {
    cal.value = eval(cal.value).toString();

  }
  catch (error) {
    cal.value = "Error";
  }
}
//for Slice
const Slice = () => {
  try {
    cal.value = cal.value.toString().slice(0, -1);
  }
  catch (error) {
    cal.value = "Error";
  }

}
//for clear the input section
const clearDisplay = () => {
  cal.value = '';
}
//Computed property for dynamic class binding
const displayClass = computed(() => {
  return cal.value.length > 12 ? 'small-text' : '';
})
</script>

<template>
  <h1>CALCULATOR</h1>
  <div class="container">
    <div class="input">
      <input type="text" v-model="cal" :class="displayClass" />
    </div>
    <div class="main_content">
      <div>
        <input @click="clearDisplay" type="button" value="C">
        <input @click="Slice()" type="button" value="X">
        <input @click="display('00')" type="button" value="00">
        <input @click="display('/')" type="button" value="/">
      </div>
      <div>
        <input @click="display('7')" type="button" value="7">
        <input @click="display('8')" type="button" value="8">
        <input @click="display('9')" type="button" value="9">
        <input @click="display('*')" type="button" value="*">
      </div>
      <div>
        <input @click="display('4')" type="button" value="4">
        <input @click="display('5')" type="button" value="5">
        <input @click="display('6')" type="button" value="6">
        <input @click="display('-')" type="button" value="-">
      </div>
      <div>
        <input @click="display('1')" type="button" value="1">
        <input @click="display('2')" type="button" value="2">
        <input @click="display('3')" type="button" value="3">
        <input @click="display('+')" type="button" value="+">
      </div>
      <div>
        <input @click="display('0')" type="button" value="0">
        <input @click="display('.')" type="button" value=".">
        <input @click="calculate()" type="button" value="=" id="equal">
      </div>
    </div>
  </div>
</template>