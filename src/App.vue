<template>
    <div>

        <router-view />
        <FooterC />
    </div>
</template>


<script>
import FooterC from './components/Footer.vue';

export default {

    components: {
        FooterC
    }
}
</script>