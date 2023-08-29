<template>
    <header class="app-header">
        <a class="logo" href="./">
            <img src="@/assets/img/logo.svg" alt="Logo">
            <img src="@/assets/img/logo-delim.svg" alt="" class="logo-delim">
            <span class="slogan">
                <dd>Find the best&nbsp;</dd>
                <dd>credit card offers online</dd>
            </span>
        </a>
        <nav class="menu">
            <ul>
                <li><a href="./">PREPAID & CREDIT OFFERS</a></li>
                <li><a href="./">RESOURCES</a></li>
            </ul>
            <form @submit.prevent="handleSearch" class="search">
                <input type="text" v-model="searchQuery" @input="handleSearch">
                <button type="submit">
                    <img src="@/assets/img/search.svg" alt="search_btn">
                </button>
            </form>
        </nav>
    </header>
</template>
  
<script>
export default {
    data() {
        return {
            searchQuery: ''
        };
    },
    methods: {
        handleSearch() {
            // Implement search logic here
            console.log('Search query:', this.searchQuery);
        }
    }
};
</script>
  
<style scoped>
.app-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 20px;
    max-width: 1440px;
    width: 100%;
    background-color: #fff;
    color: var(--font-color);
}

.logo {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    align-items: center;
    justify-content: flex-start;
    text-align: left;
    gap: 15px;
    max-width: 430px;
    word-break: break-word;
    text-decoration: none;
}

.logo img {
    height: 50px;
    width: auto;
}

.logo .slogan {
    text-decoration: none;
    color: var(--primary-color);
}

.logo img {
    height: 50px;
    width: auto;
}

.menu {
    display: flex;
    gap: 54px;
    flex-direction: row;
    flex-wrap: wrap;
    align-content: center;
    align-items: center;
}

@media screen and (max-width:1540px) {
    .logo img {
        height: 50px;
        width: auto;
    }

    .logo .slogan {
        text-decoration: none;
        color: var(--primary-color);
    }

    .menu {
        display: flex;
        gap: 54px;
        flex-direction: row;
        flex-wrap: wrap;
        align-content: center;
        align-items: center;
    }
}

@media screen and (max-width:1140px) {
    .app-header {
        padding-right: 40px;
    }

    .logo {
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;
        text-align: left;
    }

    .logo-delim {
        display: none;
    }

    .logo .slogan {
        display: flex;
        flex-direction: row;
        font-size: 12px;
    }

    .menu {
        display: flex;
        gap: 9px;
        flex-direction: column;
        flex-wrap: wrap;
        align-content: center;
        align-items: stretch;
    }

    .search {
        width: 100%;
    }

    .search input {
        width: 100%;
    }
}

@media screen and (max-width:715px) {
    .menu {
        display: flex;
        gap: 54px;
        flex-direction: row;
        flex-wrap: wrap;
        align-content: center;
        align-items: center;
    }
}

.menu ul {
    list-style: none;
    display: flex;
    gap: 54px;
}

.menu li a {
    position: relative;
    text-decoration: none;
    font-weight: bold;
    color: var(--font-color);
    line-height: 24px;
}

.menu li a::after {
    position: absolute;
    content: "";
    background-image: url("@/assets/img/keyboard-arrow-down.svg");
    width: 24px;
    height: 24px;
}

.search {
    display: flex;
    flex-direction: row;
    justify-content: stretch;
}

.search input {
    padding: 5px;
    border: 1px solid #ccc;
    outline: none;
}

.search button {
    width: 32px;
    height: 32px;
    flex-shrink: 0;
    appearance: none;
    border: none;
    cursor: pointer;
    background-color: var(--primary-color);
}

.menu li a:hover {
    text-decoration: underline;
}
</style>
  