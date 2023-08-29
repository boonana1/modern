<template>
    <div class="app-container">

        <main>
            <section class="contact-us">
                <AppBreadcrumbs :breadcrumbs="breadcrumbs" />
                <div class="container">
                    <h1>CONTACT US</h1>
                    <img src="@/assets/img/line-1.svg" alt="" class="delimiter">
                    <dd class="description">
                        We welcome your comments, questions, or any request you may<br>
                        have! If you would like to contact our
                        staff, please complete the<br>
                        form below.<br><br>
                        We will respond to your inquiries ASAP!
                    </dd>
                </div>
            </section>
            <section class="feedback">
                <h2>WRITE US</h2>
                <div class="form-container">
                    <form @submit.prevent="submitFeedback">
                        <div class="row">
                            <label for="subject">Subject:</label>
                            <AppSelect
                                :options="['Building Credit History', 'Bad Credit', 'Credit Cards for Business', 'General', 'Balance Transfer', 'Credit Card Rewards', 'Good Credit']"
                                :default="'Select Subject'" class="select" @input="feedback.subject = $event" />
                        </div>

                        <div class="row">
                            <label for="email">E-mail:</label>
                            <input type="email" id="email" v-model="feedback.email" required>
                        </div>

                        <div class="row">
                            <label for="name">Name:</label>
                            <input type="text" id="name" v-model="feedback.name" required>
                        </div>

                        <div class="row">
                            <label for="phone">Phone number:</label>
                            <input type="tel" id="phone" v-model="feedback.phone">
                        </div>

                        <div class="row">
                            <label for="question">Question:</label>
                            <textarea id="question" v-model="feedback.question" required></textarea>
                        </div>
                        <div class="submit">
                            <span>* required fields</span>
                            <button type="submit">SEND</button>
                        </div>
                    </form>
                    <dd>
                        All information submitted on this form will remain completely confidential. We <b>DO NOT sell</b>
                        names or
                        email addresses to third parties.<br><br>

                        Please review our privacy policy for further information.<br><br>

                        Please note: <br>
                        We <b>DO NOT issue credit cards</b> or have any type of personal credit card account
                        information. If you
                        have questions pertaining to an existing credit card account, please contact the bank that issued
                        the credit card directly.

                    </dd>
                </div>
            </section>
            <section class="contacts">
                <img src="@/assets/img/mail.svg" alt="" class="mail">
                <dl>
                    <h3>MAILING ADDRESS:</h3>
                    <dd>
                        1680 South Ashland Ave Suit# 3007<br>
                        Chicago, IL 60608-2013
                    </dd>
                </dl>
            </section>
            <section class="banks">
                <h2>CONTACT INFORMATION OF BANKS:</h2>
                <AppBanks :banks="banks" />
            </section>
        </main>
    </div>
</template>
  
<script>
import AppBreadcrumbs from "@/components/AppBreadcrumbs.vue";
import AppSelect from '@/components/AppSelect.vue';
import AppBanks from '@/components/AppBanks.vue';
export default {
    components: {
        AppBreadcrumbs,
        AppSelect,
        AppBanks
    },
    data() {
        return {
            feedback: {
                subject: '',
                email: '',
                name: '',
                phone: '',
                question: ''
            },
            breadcrumbs: [
                { label: "Best credit offers", route: "/" },
                { label: "Contact Us", route: "/" }
            ],
            banks: [
                { name: "BOFI:", img: "bofi.svg", phone: "800-955-7070" },
                { name: "CAPITAL ONE®:", img: "capital-one.svg", phone: "800-955-7070" },
                { name: "CAPITAL BANK:", img: "capital-bank.svg", phone: "800-955-7070" },
                { name: "CREDIT ONE BANK®:", img: "capital-one-bank.svg", phone: "800-955-7070" },
                { name: "METABANK:", img: "metabank.svg", phone: "800-955-7070" },
                { name: "MID AMERICA BANK:", img: "mid-america-bank.svg", phone: "800-955-7070" },
                { name: "SIMMONS FIRST:", img: "simmons-first.svg", phone: "800-955-7070" },
                { name: "USAA:", img: "usaa.svg", phone: "800-955-7070" }
            ],
            selectOptions: [
                { value: 'option1', label: 'Option 1' },
                { value: 'option2', label: 'Option 2' },
                { value: 'option3', label: 'Option 3' }
            ],
            selectedValue: 'option2'
        };
    },
    methods: {
        submitFeedback() {
            // You can implement the feedback submission logic here
            console.log('Feedback submitted:', this.feedback);
            // Clear the form fields after submission
            this.feedback.name = '';
            this.feedback.comment = '';
        }
    }
};
</script>
  
<style>
/* Add your CSS styles here */
.app-container {
    margin: 0;
    padding: 0;
}

main {
    padding: 20px 0;
}

.contact-us {
    background: url("@/assets/img/bg.png") right/cover, lightgray 333.054px -9.515px / 71.042% 106.479% no-repeat;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: left;
}

.contact-us>* {
    display: flex;
    flex-direction: row;
    align-items: center;
    max-width: 1440px;
    width: 100%;
    padding: 5px 20px;
}

.contact-us .container {
    padding: 65px 20px;
    gap: 30px;
}

.feedback {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: left;
    padding: 60px 0px;
    gap: 60px;
}

.feedback h2 {
    color: var(--primary-color);
}

.feedback>* {
    display: flex;
    flex-direction: row;
    align-items: center;
    max-width: 1440px;
    width: 100%;
    padding: 5px 20px;
}

.feedback .form-container {
    gap: 60px;
}

.feedback form {
    display: flex;
    flex-direction: column;
    gap: 10px;
    max-width: 700px;
    width: 100%;
}

.feedback form .row {
    display: flex;
    flex-direction: row;
    gap: 10px;
    max-width: 700px;
    width: 100%;
    align-items: stretch;
    justify-content: space-between;
}

.feedback form label {
    max-width: 140px;
}

.feedback form input,
.feedback form textarea,
.feedback form button {
    appearance: none;
    outline: none;
    font-size: 1em;
    max-width: 540px;
    width: 100%;
    color: var(--font-color);
    border: 1px solid #B3B3B3;
    line-height: 32px;
    padding-left: 10px;
}

.feedback form textarea {
    height: 140px;
    resize: none;
    font-size: 16px;
}

.feedback form button {
    width: 160px;
    height: 50px;
    flex-shrink: 0;
    border-radius: 4px;
    color: #fff;
    font-weight: bold;
    padding: 0;
    background: var(--primary-color);
}

.feedback form .submit {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: flex-start;
    justify-content: space-between;
    width: 100%;
}

.feedback form .submit span {
    color: #EF5C53;
}

.feedback dd {
    max-width: 590px;
    color: var(--font-color);
    font-family: Arial;
    font-size: 18px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
}

.contacts {
    background-color: var(--second-color);
    padding: 28px 20px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    text-align: left;
    gap: 30px;
}

.contacts img {
    width: 100px;
    height: 100px;
    background-color: var(--primary-color);
    border-radius: 100%;
}

.contacts h3 {
    padding: 13px 0px;
    color: var(--primary-color);
}

.banks {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 60px 20px;
    gap: 60px;
}
</style>
  