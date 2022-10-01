<script setup>
import Key from './Key.vue'
import Screen from './Screen.vue'
</script>

<script >
export default {
  data() {
    return {
      firstValue: "",
      secondValue: "",
      operation: null,
      result: "",
      isResolved: false
    }
  },
  methods: {
    addValue: function (value) {
      if (this.isResolved) this.clearValue();

      value = value.toString();
      
      if (this.operation == null) {
        this.firstValue += value;
      } else {
        this.secondValue += value;
      }
    },
    clearValue: function () {
      this.firstValue = "";
      this.secondValue = "";
      this.operation = null;
      this.result = "";
      this.isResolved = false;
    },
    addOperator: function (operator) {
      this.operation = operator;
    },
    evaluate: function () {
      this.result = eval(this.firstValue + this.operation + this.secondValue);
      this.isResolved = true;
    }
  }
}
</script>

<template>
  <div class="layout">
    <Screen>
      <template #keyName>{{firstValue}} {{operation}} {{secondValue}} = {{result}}</template>
    </Screen>
    <Key class="bg-yellow text-black" @click="this.clearValue">
      <template #keyName>C</template>
    </Key>
    <Key class="bg-grey text-black" @click="this.addOperator('/')">
      <template #keyName>/</template>
    </Key>
    <Key class="bg-grey text-black" @click="this.addOperator('*')">
      <template #keyName>X</template>
    </Key>
    <Key class="minus bg-magenta text-black" @click="this.addOperator('-')">
      <template #keyName>-</template>
    </Key>
    <Key @click="this.addValue('1')">
      <template #keyName>1</template>
    </Key>
    <Key @click="this.addValue('2')">
      <template #keyName>2</template>
    </Key>
    <Key @click="this.addValue('3')">
      <template #keyName>3</template>
    </Key>
    <Key @click="this.addValue('4')">
      <template #keyName>4</template>
    </Key>
    <Key @click="this.addValue('5')">
      <template #keyName>5</template>
    </Key>
    <Key @click="this.addValue('6')">
      <template #keyName>6</template>
    </Key>
    <Key class="plus bg-grey text-black" @click="this.addOperator('+')">
      <template #keyName>+</template>
    </Key>
    <Key @click="this.addValue('7')">
      <template #keyName>7</template>
    </Key>
    <Key @click="this.addValue('8')">
      <template #keyName>8</template>
    </Key>
    <Key @click="this.addValue('9')">
      <template #keyName>9</template>
    </Key>
    <Key class="zero" @click="this.addValue('0')">
      <template #keyName>0</template>
    </Key>
    <Key class="equal bg-magenta text-black" @click="this.evaluate">
      <template #keyName>=</template>
    </Key>
  </div>
</template>

<style>
.layout {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2px;
}
</style>
