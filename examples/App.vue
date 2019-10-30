<template>
  <div id="app">
    <demo></demo>
  </div>
</template>

<script>
import demo from "./demo";
export default {
  name: "app",
  components: { demo }
};
</script>

<style>
body,
h1,
h2,
h3,
h4,
h5,
h6,
a,
p,
font,
form,
ul,
li,
ol,
dl,
dd,
dt {
  margin: 0;
  padding: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Ubuntu,
    "Helvetica Neue", Helvetica, Arial, "Hiragino Sans GB", "Microsoft YaHei UI",
    "Microsoft YaHei", "PingFang SC", "Source Han Sans CN", sans-serif;
}

a {
  text-decoration: none;
  color: #000;
  -webkit-tap-highlight-color: rgba(255, 255, 255, 0);
}

a:hover {
  text-decoration: none !important;
}

a:active {
  text-decoration: none !important;
}

a:visited {
  text-decoration: none !important;
}

a:focus {
  text-decoration: none !important;
}

h1,
h2,
h3,
i,
th,
caption,
code,
address,
cite,
dfn,
em,
var {
  font-style: normal;
  font-weight: normal;
}

ul,
ol,
li,
dt,
dd {
  list-style: none;
}

img,
fieldset,
button,
input {
  border: none;
}

input,
textarea,
button,
img,
select {
  outline: none;
}

input.btn {
  outline: none;
}

hr {
  border: none;
  height: 1px;
}
</style>
