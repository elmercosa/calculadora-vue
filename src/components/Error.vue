<template>
  <div class="error">
    <span>
      <slot name="keyName"></slot>
    </span>
  </div>
</template>


<style scoped>
.error {
  grid-column: 1/5;
  background-color: #a2101c;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem;
  font-weight: bold;
  pointer-events: none;
  transition: all 0.3s ease-in-out 0.3s;
}

.v-enter-active,
.v-leave-active {
  transition: transform 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  transform: scale(0);
}

.minus {
  grid-row: 1/3;
  grid-column: 4/4;
}

.plus {
  grid-row: 3/5;
  grid-column: 4/4;
}

.zero {
  grid-column: 1/3;
}

.equal {
  grid-column: 3/5;
}
</style>
