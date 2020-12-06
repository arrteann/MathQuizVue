<template>
  <div id="btn-ctn">
    <span @click="$emit('changeoperator', '+')"> Addition </span>
    <span @click="$emit('changeoperator', '-')"> Subtraction </span>
    <span @click="$emit('changeoperator', '/')"> Division </span>
    <span @click="$emit('changeoperator', '*')"> Multiplication </span>
  </div>
</template>

<script>
export default {
  name: "Selector",
};
</script>

<style lang="scss">
#btn-ctn {
  text-align: center;
}
span {
  transition: all 0.9s ease;
  text-transform: uppercase;
  display: inline-block;
  padding: 8px 16px;
  margin: 0 10px;
  text-align: center;
  font-size: 1.2rem;
  color: #323232;
  cursor: pointer;
  vertical-align: top;
  border-radius: 2px;
  &:active,
  &:hover {
    box-shadow: 0px 3px 6px rgba($color: #000000, $alpha: 0.2);
  }
}
</style>