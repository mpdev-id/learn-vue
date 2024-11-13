<template>
 <NavbarC />
 <div class="container">
  <HeroC />
 </div>
</template>

<script>
// @ is an alias to /src
import HeroC from "@/components/Hero.vue";
import NavbarC from "@/components/Navbar.vue";

export default {
 name: "HomeView",
 components: {
  NavbarC,
  HeroC,
 },
};
</script>
