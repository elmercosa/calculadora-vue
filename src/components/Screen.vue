<template>
  <div class="screen">
    <span>
      <slot name="keyName"></slot>
    </span>
  </div>
</template>


<style scoped>
.screen {
  grid-column: 1/5;
  background-color: white;
  color: black;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem;
  font-weight: bold;
  pointer-events: none;
  transition: all 0.3s ease-in-out;
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
