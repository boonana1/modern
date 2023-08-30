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
            <button class="menu-toggler" @click="menuToggle">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
                    <g clip-path="url(#clip0_1_3896)">
                        <path d="M3 18H21V16H3V18ZM3 13H21V11H3V13ZM3 6V8H21V6H3Z" fill="white" />
                    </g>
                    <defs>
                        <clipPath id="clip0_1_3896">
                            <rect width="24" height="24" fill="white" />
                        </clipPath>
                    </defs>
                </svg>
            </button>
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
            console.log('Search query:', this.searchQuery);
        },
        menuToggle() {
            document.querySelector(".menu ul").classList.toggle("opened");
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

.menu-toggler {
    display: none;
    padding: 5px;
    flex-shrink: 0;
    background: #005898;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    outline: none;
    font-size: 1em;
    border: none;
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
        gap: 14px;
        flex-direction: row;
        flex-wrap: wrap;
        align-content: center;
        align-items: center;
    }

    .search {
        width: auto;
    }

    .search input {
        width: auto;
    }

    .menu ul {
        display: none;
    }

    .menu ul.opened {
        position: absolute;
        display: flex;
        flex-direction: column;
        top: 0;
        padding: 20px;
        left: 0;
        background: #fff;
    }

    .menu-toggler {
        display: flex;
    }

    .search input {
        display: none;
    }
}
</style>
  