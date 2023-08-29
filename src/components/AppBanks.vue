<template>
    <div class="banks-container">
        <div v-for="(bank, i) in banks" :key="i">
            <img :src="require(`@/assets/img/${bank.img}`)" alt="">
            <img src="@/assets/img/line-2.svg" alt="">
            <dl>
                <h3>{{ bank.name }}</h3>
                <dd>
                    Customer Service:<br>
                    <b>{{ bank.phone }}</b>
                </dd>
            </dl>
        </div>
    </div>
</template>
  
<script>
export default {
    components: {
    },
    props: {
        banks: {
            type: Array,
            required: true
        },
        image: {
            type: String,
            required: true
        }
    }
};
</script>
  
<style scoped>
.banks-container {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(2, 1fr);
    grid-column-gap: 0px;
    grid-row-gap: 0px;
    margin: 10px 0;
    font-size: 16px;
    max-width: 1440px;
    width: 100%;
    gap: 60px;
}

@media screen and (max-width:1540px) {
    .banks-container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: repeat(3, 1fr);
    }
}

@media screen and (max-width:1080px) {
    .banks-container {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-template-rows: repeat(4, 1fr);
    }
}

@media screen and (max-width:715px) {
    .banks-container {
        display: grid;
        grid-template-columns: repeat(1, 1fr);
        grid-template-rows: repeat(8, 1fr);
    }
}

.banks-container>div {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    min-width: 300px;
    flex-grow: 1;
}

.banks-container h3 {
    color: var(--primary-color);
}

.banks-container a+div {
    display: block;
    text-align: center;
    width: 16px;
    height: 16px;
}
</style>
  