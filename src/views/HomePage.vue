<template>
    <div class="app-container">

        <main>
            <section class="contact-us">
                <AppBreadcrumbs :breadcrumbs="breadcrumbs" />
                <div class="container">
                    <h1>CONTACT US</h1>
                    <img src="@/assets/img/line-1.svg" alt="" class="delimiter right">
                    <img src="@/assets/img/line-1-bottom.svg" alt="" class="delimiter bottom">
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
                <div class="form-container">
                    <h2>WRITE US</h2>
                    <form @submit.prevent="submitFeedback">
                        <div class="row">
                            <label for="subject">Subject<span style="color:var(--error-color);">*</span>:</label>
                            <AppSelect
                                :options="['Building Credit History', 'Bad Credit', 'Credit Cards for Business', 'General', 'Balance Transfer', 'Credit Card Rewards', 'Good Credit']"
                                :default="'Select Subject'" class="select" @input="feedback.subject = $event" />
                        </div>

                        <div class="row">
                            <label for="email">E-mail<span style="color:var(--error-color);">*</span>:</label>
                            <input type="email" id="email" v-model="feedback.email">
                        </div>

                        <div class="row">
                            <label for="name">Name<span style="color:var(--error-color);">*</span>:</label>
                            <input type="text" id="name" v-model="feedback.name">
                        </div>

                        <div class="row">
                            <label for="phone">Phone number:</label>
                            <input type="tel" id="phone" @input="phoneMask" v-model="feedback.phone" maxlength="14"
                                placeholder="1-XXX-XXX-XXXX">
                        </div>

                        <div class="row">
                            <label for="question">Question<span style="color:var(--error-color);">*</span>:</label>
                            <textarea id="question" v-model="feedback.question"></textarea>
                        </div>
                        <div class="submit">
                            <span>* required fields</span>
                            <button type="submit">SEND</button>
                        </div>
                    </form>
                </div>
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
            console.log('Feedback submitted:', this.feedback);
            console.log(`Questions from DreamCreditMaker: ${this.feedback.subject}`);
            console.log(`Email: ${this.feedback.email}\nName: ${this.feedback.name}\nQuestion: ${this.feedback.question}\nPhone Number: ${this.feedback.phone}`);
            if (this.feedback.subject == 'Select Subject' || this.feedback.email == "" || this.feedback.name == "" || this.feedback.question == "") {
                document.querySelector(".form-container").classList.add("error");
            } else {
                // fetch('https://path-to-modern-mail.com/index.php', {
                //     method: 'POST',
                //     body: JSON.stringify({
                //         "subject": this.feedback.subject,
                //         "email": this.feedback.email,
                //         "name": this.feedback.name,
                //         "question": this.feedback.question,
                //         "phone": this.feedback.phone
                //     })
                // }).then(res => res.json()).then(res => {
                let formContainer = document.querySelector(".form-container");
                let modal = document.createElement("div");
                let modalHeading = document.createElement("h3");
                let modalDesc = document.createElement("span");
                let modalClose = document.createElement("button");
                modal.classList.add("modal-success");
                modalClose.classList.add("modal-success-close");
                modalHeading.innerText = "Thanks for your question!";
                modalDesc.innerText = "Our experts will reply you by email as soon as possible.";
                modal.appendChild(modalHeading);
                modal.appendChild(modalDesc);
                modal.appendChild(modalClose);
                document.addEventListener("click", function close(e) {
                    if (e.target.className == "modal-success-close" || e.target.className != "modal-success") {
                        modal.remove();
                        document.removeEventListener("click", close);
                    }
                })
                formContainer.appendChild(modal);
                setTimeout(() => {
                    modal.remove();
                }, 3000);
                formContainer.classList.remove("error");
                this.feedback.name = '';
                this.feedback.email = '';
                this.feedback.question = '';
                this.feedback.phone = '';
                // })
            }
        },
        phoneMask() {
            let phone = this.feedback.phone;
            phone = phone.replace(/\D/g, '');
            phone = phone.replace(/^(\d{0,1})(\d{0,3})(\d{0,3})(\d{0,4})$/, '$1-$2-$3-$4');
            this.feedback.phone = phone;
        }
    }
};
</script>
  
<style>
.app-container {
    margin: 0;
    padding: 0;
}


.contact-us {
    background: url("@/assets/img/bg.png") 65%/cover, lightgray 333.054px -9.515px / 71.042% 106.479% no-repeat;
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
    flex-direction: row;
    align-items: center;
    text-align: left;
    padding: 60px 20px;
    gap: 60px;
    max-width: 1440px;
    width: 100%;
    margin: 0 auto;
}

.feedback h2 {
    color: var(--primary-color);
}

.feedback>* {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 5px 0px;
    max-width: 700px;
    width: 100%;
}

.feedback .form-container {
    gap: 60px;
}

.feedback .form-container label {
    font-size: 18px;
}

.feedback .form-container label+* {
    font-size: 16px;
}

.feedback form {
    display: flex;
    flex-direction: column;
    gap: 20px;
    max-width: 700px;
    width: 100%;
}

.feedback form .row {
    display: grid;
    gap: 10px;
    max-width: 700px;
    width: 100%;
    align-items: stretch;
    grid-template-columns: auto 1fr;
    justify-items: end;
    justify-content: space-between;
}

.feedback form label {
    max-width: 140px;
    line-height: 32px;
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

.feedback form input::placeholder {
    color: #B3B3B3;
}

.feedback .error form input:not(#phone),
.feedback .error form textarea {
    color: var(--error-color);
    border: 1px solid var(--error-color);
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
    max-width: 540px;
    align-self: flex-end;
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

.contact-us .delimiter.right {
    display: block;
}

.contact-us .delimiter.bottom {
    display: none;
}

.modal-success {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 500px;
    background: var(--modal-color);
    text-align: center;
    padding: 35px;
}

.modal-success h3 {
    color: var(--error-color);
    margin-bottom: 20px;
}

.modal-success-close {
    position: absolute;
    display: block;
    background: url(http://localhost:8080/img/Vector.d21e7102.svg)no-repeat center, var(--modal-button-color);
    width: 27px;
    height: 27px;
    border: none;
    cursor: pointer;
    left: 100%;
    top: 0;

}

.contact-us dd,
.feedback dd {
    font-size: 18px;
}

footer {
    font-size: 14px;
}

@media screen and (max-width:1540px) {}

@media screen and (max-width:1080px) {

    .app-breadcrumbs {
        display: none;
    }

    .feedback {
        padding: 40px 0px;
        gap: 40px;
        flex-direction: column;
    }

    .feedback>* {
        padding: 0px 20px;
    }

    .contact-us dd,
    .feedback dd {
        font-size: 16px;
    }

    .feedback dd {
        max-width: unset;
        width: 100%;
        display: block;
    }

    .feedback .form-container {
        flex-direction: column;
        gap: 40px;
        align-items: stretch;
        max-width: unset;
    }

    .feedback form {
        gap: 20px;
        max-width: unset;
    }

    .feedback form .row {
        max-width: unset;
    }

    .app-breadcrumbs {
        display: none;
    }

    .contact-us {
        background: url("@/assets/img/bg.png") 70%/cover, lightgray 333.054px -9.515px / 71.042% 106.479% no-repeat;
    }

    .contact-us .container {
        padding: 25px 20px;
        gap: 20px;
    }

    .description {
        max-width: 340px;
    }

    .banks {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 40px 60px;
        gap: 40px;
    }
}

@media screen and (max-width:715px) {
    .feedback .form-container {
        flex-direction: column;
        gap: 20px;
    }

    .feedback .form-container label {
        font-size: 14px;
        line-height: 14px;
    }

    .feedback .form-container label+* {
        font-size: 14px;
    }

    .contact-us dd,
    .feedback dd {
        font-size: 14px;
    }

    .contact-us {
        background: url("@/assets/img/bg.png") 45%/cover, lightgray 333.054px -9.515px / 71.042% 106.479% no-repeat;
    }

    .contact-us>* {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
    }

    .contact-us .container {
        padding: 30px 16px;
        gap: 10px;
    }

    .contact-us .delimiter.right {
        display: none;
    }

    .contact-us .delimiter.bottom {
        display: block;
    }

    .feedback {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        padding: 30px 0px;
        gap: 20px;
        margin: 0 auto;
    }

    .feedback>* {
        justify-content: center;
    }

    .feedback form {
        gap: 20px;
    }

    .feedback form .row {
        display: grid;
        gap: 10px;
        max-width: 700px;
        width: 100%;
        grid-template-columns: 1fr;
        justify-items: start;
    }

    .feedback form .submit {
        align-self: center;
        align-items: center;
        max-width: unset;
    }

    .feedback form .row label+* {
        max-width: 100%;
    }

    .modal-success {
        max-width: 290px;
        width: 100%;
    }

    .modal-success h3 {
        margin-bottom: 10px;
    }

    .modal-success-close {
        left: 90.5%;
    }

    .contacts {
        padding: 28px 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        text-align: left;
        gap: 20px;
    }

    .contacts {
        text-align: center;
    }

    .banks {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 30px 10px;
        gap: 20px;
    }
}
</style>
  