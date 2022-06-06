<template>
  <nav>
    <h1>TVStatic</h1>
    <ul>
      <li><RouterLink to="/">Home</RouterLink></li>
      <li><RouterLink to="/search">Search</RouterLink></li>
      <li><RouterLink to="/browse">Browse</RouterLink></li>
    </ul>
  </nav>
</template>

<script>
import { RouterLink } from "vue-router";

export default{
  components: {
    RouterLink: RouterLink
  }
}
</script>

<style scoped>
nav {
  display: flex;
  color: var(--white);
  background-color: var(--black);
  align-items: center;
  padding: 0 20px;
}
nav h1 {
  font-weight: lighter;
  font-size: 40px;
}
nav ul {
  list-style: none;
  display: flex;
  width: 30vw;
  justify-content: space-around;
}
nav a {
  font-weight: bold;
  color: var(--white);
  text-decoration: none;
  transition: 0.15s linear;
}
nav a:hover {
  color: var(--red);
}

@media only screen and (max-width: 600px){
  nav{
    display: flex;
    justify-content: center;
  }
  nav ul{
    width: 60vw;
  }
}
</style>
