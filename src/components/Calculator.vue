<script setup>
import Key from './Key.vue'
import Screen from './Screen.vue'
</script>

<script >
export default {
  data() {
    return {
      firstValue: "hola",
      secondValue: "",
      operation: null
    }
  },
  methods: {
    addValue: function (value) {
      if (this.operation != null) {
        this.firstValue += value;
      } else {
        this.secondValue += value;
      }
    },
    clearValue: function () {
      this.firstValue = "";
      this.secondValue = "";
      this.operation = null;
      console.log('obj:',"obj");
    }
  }
}
</script>

<template>
  <div class="layout">
    <Screen>
      <template #keyName>{{firstValue}}</template>
    </Screen>
    <Key class="bg-yellow text-black" @click="this.clearValue()">
      <template #keyName>C</template>
    </Key>
    <Key class="bg-grey text-black">
      <template #keyName>/</template>
    </Key>
    <Key class="bg-grey text-black">
      <template #keyName>X</template>
    </Key>
    <Key class="minus bg-magenta text-black">
      <template #keyName>-</template>
    </Key>
    <Key>
      <template #keyName>1</template>
    </Key>
    <Key>
      <template #keyName>2</template>
    </Key>
    <Key>
      <template #keyName>3</template>
    </Key>
    <Key>
      <template #keyName>4</template>
    </Key>
    <Key>
      <template #keyName>5</template>
    </Key>
    <Key>
      <template #keyName>6</template>
    </Key>
    <Key class="plus bg-grey text-black">
      <template #keyName>+</template>
    </Key>
    <Key>
      <template #keyName>7</template>
    </Key>
    <Key>
      <template #keyName>8</template>
    </Key>
    <Key>
      <template #keyName>9</template>
    </Key>
    <Key class="zero">
      <template #keyName>0</template>
    </Key>
    <Key class="equal bg-magenta text-black">
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
