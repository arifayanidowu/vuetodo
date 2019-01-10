<template>
  <div id="app">
    <Header/>
    <router-view/>
  </div>
</template>

<script>
import Header from "@/components/layout/Header";
export default {
  name: "app",
  components: {
    Header
  }
};
</script>


<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Dosis", sans-serif;
  line-height: 1.4;
}
.text-center {
  text-align: center;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}

img {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  margin: 0 auto;
}

.align-center {
  text-align: center;
  margin: 0 auto;
  position: absolute;
  top: 25%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
