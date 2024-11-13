<template>
    <div>
        <!-- laptop -->
        <div>
            <div class="row py-5 d-none d-md-flex">
                <div class="col-md-6 align-content-center">
                    <h2>
                        Order And
                        <strong class="text-info">Wait 5 Minutes <i
                                class="bi bi-calendar-heart"></i></strong>
                    </h2>
                    <h3>All easy with us</h3>
                    <router-link to="food" class="mt-3 btn btn-info shadow-lg">Order Here <i
                            class="bi bi-chat-dots"></i></router-link>
                </div>

                <div class="col-md-6">
                    <img class="w-75" src="@/assets/imgs/hero.svg" alt="Hero"
                        srcset="@/assets/imgs/hero.svg" />
                </div>
            </div>
        </div>

        <!-- mobile -->
        <div>
            <div class="row py-2 d-flex flex-column-reverse d-md-none text-center">
                <div class="col-md-6 align-content-center">
                    <strong>
                        Order And
                        <strong class="text-info">Wait 5 Minutes <i
                                class="bi bi-calendar-heart"></i></strong>
                    </strong>
                    <h5>All easy with us</h5>
                    <p>Lorem ipsum dolor </p>
                    <router-link to="food" class="mt-3 btn btn-info shadow-lg">Order Here <i
                            class="bi bi-chat-dots"></i></router-link>
                </div>

                <div class="col-md-6">
                    <img class="w-75" src="@/assets/imgs/hero.svg" alt="Hero"
                        srcset="@/assets/imgs/hero.svg" />
                </div>
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
