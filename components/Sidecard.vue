<template>
  <div class="sidecard">
    <div class="info left">
      <h2><slot name="title">Title</slot></h2>
      <p>
        <slot name="summary">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum, iusto?
        </slot>
      </p>

     

      
    </div>

    <div class="image right">
      <slot name="image"><img src="https://assets.codepen.io/5737230/placeholder.png" class="showimage"/></slot>
    </div>
  </div>
</template>

<script></script>

<style scoped>
.sidecard {
  width: 30vw;
    height: 20vw;
  display: flex;
  flex-direction: row;
  /*   border: 3px solid #0a0a0a; */
  border-radius: 10px;
  box-shadow: 1px 1px 5px #000;
  margin: 10px;
  overflow: hidden;
  color: #dcdcdc;
  background-color: #0a0a0a;
  transition: .1s linear;
}
.sidecard:hover{
  transform: scale(1.05);
  box-shadow: 4px 4px 8px #000;
}
.left {
  width: 50%;
}
.left h2{
  margin: 0;
  font-size: 18px;
}
.right {
  width: 50%;
  display: flex;
  justify-content: flex-end;
}
.right img{
    height: 100%;
}
.info {
  display: flex;
  flex-direction: column;
  padding: 15px;
  justify-content: space-between;
}
.genres {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  font-weight: bold;
}
.network-website {
  display: flex;
  justify-content: space-between;
}
.buttons {
  display: flex;
  justify-content: space-around;
}
.image{
    height: 20vw;
}
.image img {
  height: 20vw;
}


</style>
