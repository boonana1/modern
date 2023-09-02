<template>
    <div class="app-breadcrumbs">
        <span v-for="(crumb, i) in breadcrumbs" :key="i">
            <router-link :to="crumb.route">{{ crumb.label }}</router-link>
            <img v-if="i < breadcrumbs.length - 1" src="@/assets/img/chevron-right.svg" alt="">
        </span>
    </div>
</template>
  
<script>
import { RouterLink } from 'vue-router'
export default {
    components: {
        RouterLink
    },
    props: {
        breadcrumbs: {
            type: Array,
            required: true
        }
    }
};
</script>
  
<style scoped>
.app-breadcrumbs {
    margin: 10px 0;
    font-size: 14px;
}

.app-breadcrumbs>span {
    display: flex;
}

.app-breadcrumbs a {
    text-decoration: underline;
    color: var(--font-color);
}

.app-breadcrumbs a:hover {
    text-decoration: underline;
}

.app-breadcrumbs a+span {
    display: block;
    text-align: center;
    width: 16px;
    height: 16px;
}

@media screen and (max-width:1080px) {

    .app-breadcrumbs {
        display: none;
    }
}
</style>
  