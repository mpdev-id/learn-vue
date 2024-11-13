<template>
 <div class="col-12">
  <div class="row">
   <div class="md-col-6 align-content-center">
    <h2>
     Order And
     <strong class="text-info"
      >Wait 5 Minutes <i class="bi bi-calendar-heart"></i
     ></strong>
    </h2>
    <h3>All easy with us</h3>
    <router-link to="food" class="mt-3 btn btn-info shadow-lg"
     >Order Here <i class="bi bi-chat-dots"></i
    ></router-link>
   </div>

   <div class="md-col-6">
    <img
     class="w-50"
     src="@/assets/imgs/hero.svg"
     alt="Hero"
     srcset="@/assets/imgs/hero.svg"
    />
   </div>
  </div>
 </div>
</template>

<script>
export default {
 name: "HeroC",
};
</script>

<style></style>
