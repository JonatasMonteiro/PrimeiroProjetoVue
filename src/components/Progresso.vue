<template>
  <div class="borda">
    <div :style="{ width: porcentagem + 'px' }" class="barra">
      {{ porcentagem / 10 }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    porcentagem: Number(0)
  }
};
</script>

<style>
.borda {
  width: 1000px;
  height: 30px;
  border-radius: 10px;
  border: 2px solid white;
}

.barra {
  border-radius: 10px;
  height: 30px;
  background: green;
}
</style>
