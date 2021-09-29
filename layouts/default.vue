<template>
    <div class="app-container">

        <TheHeader/>

        <div class="app-content">
            <nuxt />
        </div>

        <TheFooter/>

    </div>
</template>

<script>
    import TheHeader from '~/components/TheHeader'
    import TheFooter from '~/components/TheFooter'
    export default {
        components: {
            TheHeader,
            TheFooter
        },
    }
</script>
