<template>
    <div class="primary-nav">
        <a class="logo" href="./">
            <img src="@/assets/img/footer-logo.svg" alt="Logo">
            <img src="@/assets/img/logo-delim.svg" alt="" class="logo-delim">
            <span class="slogan">
                <dd>Find the best&nbsp;</dd>
                <dd>credit card offers online</dd>
            </span>
        </a>
        <hr>
        <nav class="footer-menu">
            <ul>
                <li><router-link to="/">About us</router-link></li>
                <li><router-link to="/">Contact us</router-link></li>
                <li><router-link to="/">Privacy</router-link></li>
                <li><router-link to="/">Terms & Conditions</router-link></li>
                <li><router-link to="/">Sitemap</router-link></li>
            </ul>
        </nav>
    </div>
    <div class="second-nav">
        <span class="copyright">
            Copyright © 2015 DreamCreditMaker.com.<br>
            All Rights Reserved.
        </span>
        <nav class="social">
            <ul>
                <li><span>FOLLOW US:</span></li>
                <li><router-link to="/"><img src="@/assets/img/ic-24-facebook.svg" alt="Facebook"></router-link></li>
                <li><router-link to="/"><img src="@/assets/img/ic-24-twitter.svg" alt="Twitter"></router-link></li>
                <li><router-link to="/"><img src="@/assets/img/ic-24-google.svg" alt="Google"></router-link></li>
            </ul>
        </nav>
    </div>
    <hr>
    <div class="note">
        *See the credit card's terms and conditions on the online application page. Note that this website may be
        compensated by credit card issuers when the visitor applies for a card through the links on this website. We do our
        best to maintain all information accurate and up to date. However, we do not warrant the credit card information
        won't change. Click the "Apply Online" button and review the current info on the secure credit card terms
        page.<br><br>

        Information in these articles is brought to you by DreamCreditMaker.com. Banks, issuers, and credit card companies
        mentioned in the articles do not endorse or guarantee, and are not responsible for, the contents of the
        articles.<br><br>

        * The DreamCreditMaker.com webpage is a free service and an information resource for credit cards and financial
        products and services available to eligible United States consumers. DreamCreditMaker.com does not offer any
        warranties and is not a direct service. There are no guarantees for approval or offers when applying for a credit
        card. Please refer to the application if you would like more information on each credit card. When you click "Apply"
        for a particular credit card, please take the time to review the terms and conditions of the product/service at the
        issuer's website. All logos on the DreamCreditMaker.com website are property of their respective owners.<br><br>

        This website may be compensated by the credit card issuers when people apply for a credit card using the links on
        this website. We strive to maintain the information accurate on the website. However, the credit card information is
        subject to change. Therefore, we recommend you to click the "Apply Now" button to review the up to date credit
        card's terms and conditions.<br><br>

        DreamCreditMaker.com is an independent, advertising-supported web site. The offers that appear on our site are from
        credit card issuers and companies from which DreamCreditMaker.com receives compensation. This compensation may
        impact how and where credit products appear on our site, including, for example, the order in which they may appear
        within listings on separate pages of our web site. DreamCreditMaker.com does not present or review all available
        credit products.<br><br>

        Please note that DreamCreditMaker.com has financial relationships with some of the merchants mentioned here.
        DreamCreditMaker.com may be compensated if consumers choose to utilize the links located throught the content on
        this site and generate sales for the said merchant.
    </div>
</template>
  
<script>
import { RouterLink } from 'vue-router'
export default {
    components: {
        RouterLink
    }
};
</script>
  
<style scoped>
.primary-nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5px 20px;
    max-width: 1440px;
    width: 100%;
}

.second-nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5px 20px;
    max-width: 1440px;
    width: 100%;
}

.primary-nav hr {
    display: none;
}

.logo img {
    height: 50px;
    width: auto;
}

.logo .logo-delim {
    display: none;
}

.logo .slogan {
    display: none;
    text-decoration: none;
    color: var(--primary-color);
}

.footer-menu {
    display: flex;
    gap: 54px;
    flex-direction: row;
    flex-wrap: wrap;
    align-content: center;
    align-items: center;
    padding: 0;
}

.footer-menu ul {
    list-style: none;
    display: flex;
    gap: 54px;
    row-gap: 12px;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: flex-end;
}

.footer-menu li a {
    position: relative;
    text-decoration: none;
    font-weight: bold;
    line-height: 24px;
}

.social {
    display: flex;
    gap: 54px;
    flex-direction: row;
    flex-wrap: wrap;
    align-content: center;
    align-items: center;
    padding: 0px 0px;
}

.social span {
    font-weight: bold;
}

.social ul {
    list-style: none;
    display: flex;
    gap: 10px;
    flex-direction: row;
    align-content: center;
    align-items: center;
}

.social li a {
    position: relative;
    text-decoration: none;
    font-weight: bold;
    line-height: 24px;
}

.footer-menu li a:hover {
    text-decoration: underline;
}

hr {
    width: 100%;
    /* margin: 21px 0px; */
    border-color: #262626;
    height: 4px;
}

.note {
    padding: 5px 20px;
    max-width: 1440px;
    color: #FFF;
    font-family: Arial;
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    padding-bottom: 60px;
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
}

@media screen and (max-width:1140px) {

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
        font-size: 12px;
    }
}

@media screen and (max-width:600px) {
    .primary-nav {
        flex-direction: column;
        gap: 20px;
        padding: 0;
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
        height: 50px;
    }

    .logo img {
        height: 30px;
        width: auto;
    }

    .logo .logo-delim {
        display: block;
    }

    .logo .slogan {
        display: flex;
        flex-direction: column;
        font-size: 12px;
    }

    .footer-menu ul {
        flex-wrap: wrap;
        justify-content: center;
    }

    .primary-nav hr {
        display: block;
    }

    .second-nav {
        gap: 30px;
        flex-direction: column-reverse;
    }
}
</style>
  