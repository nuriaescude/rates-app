<template>
    <header>
        <div class="brand-name">
            <nuxt-link 
                tag="img"
                class="logo__img"
                :src="require('~/assets/lamp_icon.svg')" 
                to="/">
            </nuxt-link>
        </div>
    </header>
</template>

<style scoped lang="scss">
header{
    position: relative;
    display: grid;
    grid-template: 60px / auto 1fr;
    align-items: center;
    box-shadow: 0 5px 5px 0 rgba(0,0,0,.13);
    background-color: $white-base;
    padding: 0 1.5rem;
    width: 100%;
    height: 4.25rem;
    .brand-name 
        a {
            margin: 0 10px;
            font-size: 1.3rem;
            color: $gray-dark;
        }
        .logo__img {
            height: 2rem;
            cursor: pointer;
        }
}
    
@media (max-width: 767px) {
    header{
        padding: 0 16px;
    }
}
@media (min-width: 768px) {
    header{
        padding: 0 64px;
    }
}
</style>