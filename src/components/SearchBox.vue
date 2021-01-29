<template>
  <div>
    <input class="card"/>
    <span></span>
    <a href='#' class='weak'>Scan Barcode</a>
  </div>
</template>

<script>
export default {
  name: "SearchBox",
};
</script>

<style scoped>
div {
  position: relative;
}

input {
  position: relative;
  box-sizing: border-box; 
  width: 100%;
  padding-left: 50px;
  padding-right: 130px;
}
input:focus {
  outline: none;
}

span {
  position: absolute;
  height: 7px;
  width: 7px;
  background: transparent;
  border: 2px solid var(--faint-strong);
  left: 19px;
  top: 15px;
  border-radius: 100%;
}
span:after {
  content: "";
  position: absolute;
  background: var(--faint-strong);
  height: 4px;
  width: 2px;
  bottom: -4px;
  right: -2px;
  transform: rotate(-45deg);
}
a {
  position: absolute;
  right: 19px;
  top: 15px;
  font-size: 90%;
}
</style>

// https://codepen.io/FUGU22/pen/RgBydE