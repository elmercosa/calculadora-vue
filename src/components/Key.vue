<template>
  <div class="key bg-blue">
    <span>
      <slot name="keyName"></slot>
    </span>
  </div>
</template>


<style scoped>
.key {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}

.minus {
  grid-row: 2/4;
  grid-column: 4/4;
}

.plus {
  grid-row: 4/6;
  grid-column: 4/4;
}

.zero {
  grid-column: 1/3;
}

.equal {
  grid-column: 3/5;
}

</style>
