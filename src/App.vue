<script setup>
import { ref } from "vue";
let data = ref({
  nom: "Nom",
  prenom: "Prénom",
  mail: "mail@outsourcia-group.com",
  fonction: "Fonction",
  consentement: false,
  pays: {
    MAROC: {
      fixe: "+212 5 22 99 99 99",
      mobile: "+212 6 99 99 99 99",
      adresse: "217, Boulevard Anfa",
      cp: "21000 Casablanca",
    },
    FRANCE: {
      fixe: "+33 1 99 99 99 99",
      mobile: "+33 9 99 99 99 99",
      adresse: "23, rue Lavoisier",
      cp: "27 000 Evreux",
    },
  },
});
function copy() {
  let elem = document.querySelector("#signature");
  let str = elem.innerHTML;
  function listener(e) {
    let add =
      "<div><style>.signature a {text-decoration: none !important;}</style></div><br />";
    e.clipboardData.setData("text/html", add + str);
    e.clipboardData.setData("text/plain", add + str);
    e.preventDefault();
  }
  document.addEventListener("copy", listener);
  document.execCommand("copy");
  document.removeEventListener("copy", listener);
}
</script>
<template>
  <div class="flex items-center mx-auto justify-center p-12">
    <div class="w-full max-w-[550px] bg-white">
      <form class="py-6 px-9" action="" method="POST" @submit.prevent="copy">
        <div class="mb-5">
          <label
            for="email"
            class="mb-3 block text-base font-medium text-[#07074D]"
          >
            Adresse mail :
          </label>
          <input
            id="email"
            type="email"
            v-model="data.mail"
            class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
          />
        </div>

        <div class="mb-5">
          <label
            for="nom"
            class="mb-3 block text-base font-medium text-[#07074D]"
          >
            nom
          </label>
          <input
            id="nom"
            type="text"
            v-model="data.nom"
            class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
          />
        </div>
        <div class="mb-5">
          <label
            for="prenom"
            class="mb-3 block text-base font-medium text-[#07074D]"
          >
            prenom
          </label>
          <input
            id="prenom"
            type="text"
            v-model="data.prenom"
            class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
          />
        </div>
        <div class="mb-5">
          <label
            for="fonction"
            class="mb-3 block text-base font-medium text-[#07074D]"
          >
            fonction
          </label>
          <input
            id="fonction"
            type="text"
            v-model="data.fonction"
            class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
          />
        </div>
        MAROC :
        <div class="mb-5">
          <label
            for="fixemaroc"
            class="mb-3 block text-base font-medium text-[#07074D]"
          >
            fixe
          </label>
          <input
            id="fixemaroc"
            type="text"
            v-model="data.pays.MAROC.fixe"
            class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
          />
        </div>
        <div class="mb-5">
          <label
            for="mobilemaroc"
            class="mb-3 block text-base font-medium text-[#07074D]"
          >
            mobile
          </label>
          <input
            id="mobilemaroc"
            type="text"
            v-model="data.pays.MAROC.mobile"
            class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
          />
        </div>
        FRANCE :
        <div class="mb-5">
          <label
            for="fixefrance"
            class="mb-3 block text-base font-medium text-[#07074D]"
          >
            fixe
          </label>
          <input
            id="fixefrance"
            type="text"
            v-model="data.pays.FRANCE.fixe"
            class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
          />
        </div>
        <div class="mb-5">
          <label
            for="mobilefrance"
            class="mb-3 block text-base font-medium text-[#07074D]"
          >
            mobile
          </label>
          <input
            id="mobilefrance"
            type="text"
            v-model="data.pays.FRANCE.mobile"
            class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
          />
        </div>

        <div class="mb-5">
          <label
            for="consentement"
            class="mb-3 block text-base font-medium text-[#07074D]"
          >
            consentement
          </label>
          <input
            id="consentement"
            type="checkbox"
            v-model="data.consentement"
          />
        </div>
        <div>
          <button
            @click="copy"
            class="hover:shadow-form w-full rounded-md bg-[#6A64F1] py-3 px-8 text-center text-base font-semibold text-white outline-none"
          >
            Copy
          </button>
        </div>
      </form>
    </div>
    <div id="signature" style="min-width: 700px">
      <table
        class="signature"
        cellspacing="0"
        cellpadding="0"
        style="font-size: 11px; font-weight: 400; letter-spacing: normal"
        border="0"
      >
        <tr>
          <td style="padding: 0px 1px 0px 0px">
            <table
              cellspacing="0"
              cellpadding="0"
              border="0"
              style="width: 100%; border-spacing: 0; vertical-align: middle"
            >
              <tbody>
                <tr>
                  <td
                    valign="middle"
                    style="
                      vertical-align: middle;
                      border-right: 1px solid #ff8f1f;
                      padding-right: 40px;
                      height: 60px;
                    "
                  >
                    <p
                      style="
                        margin: 1px;
                        color: #ff8f1f;
                        font-size: 14px;
                        font-weight: 700;
                      "
                      v-text="data.prenom + ' ' + data.nom"
                    ></p>
                    <p style="margin: 1px">
                      <a
                        :href="'mailto:' + data.mail"
                        style="
                          font-family: Arial, sans-serif;
                          font-size: 13px;
                          line-height: 17px;
                          white-space: nowrap;
                          color: #454556;
                          text-decoration: none !important;
                        "
                        ><span
                          style="
                            font-family: Arial, sans-serif;
                            font-size: 13px;
                            line-height: 17px;
                            white-space: nowrap;
                            color: #454556;
                            text-decoration: none !important;
                          "
                          v-text="data.mail"
                        ></span
                      ></a>
                    </p>
                  </td>
                  <td style="border-right: 1px solid #ff8f1f; padding: 0 20px">
                    <p
                      style="
                        font-family: Arial, sans-serif;
                        text-align: center;
                        min-width: 200px;
                        font-weight: 700;
                        line-height: 16px;
                      "
                      v-text="data.fonction"
                    ></p>
                  </td>
                  <td style="padding-left: 40px">
                    <img
                      src="https://outsourcia-signature.netlify.app/assets/logo.png"
                      alt="Logo OUTSOURCIA"
                    />
                  </td>
                </tr>
              </tbody>
            </table>
          </td>
        </tr>
        <tr>
          <td>
            <table
              cellspacing="0"
              cellpadding="0"
              border="0"
              style="
                width: 100%;
                white-space: nowrap;
                border-spacing: 0;
                margin-top: 10px;
                font-size: 11px;
                font-weight: 400;
                line-height: 15px;
              "
            >
              <tr>
                <template v-for="(d, pay) in data.pays" :index="pay">
                  <td style="padding-right: 10px">
                    <span
                      style="color: #ff8f1f; font-size: 12px; font-weight: 500"
                      >{{ pay }}</span
                    >
                  </td>
                  <td style="color: #83818a; font-size: 12px; font-weight: 600">
                    <p style="margin: 1px">
                      <img
                        v-if="d.fixe"
                        style="margin-right: 5px"
                        alt="phone"
                        src="https://outsourcia-signature.netlify.app/assets/icons/phone.png"
                      />
                      <span
                        v-if="d.fixe"
                        style="margin-right: 10px; white-space: nowrap"
                        v-text="d.fixe"
                      ></span>
                      <img
                        v-if="d.mobile"
                        style="margin-right: 5px; white-space: nowrap"
                        alt="phone"
                        src="https://outsourcia-signature.netlify.app/assets/icons/smartphone.png"
                      />
                      <span
                        v-if="d.mobile"
                        style="white-space: nowrap"
                        v-text="d.mobile"
                      ></span>
                    </p>
                    <p style="margin: 1px">
                      <img
                        style="margin-right: 5px"
                        alt="geo"
                        src="https://outsourcia-signature.netlify.app/assets/icons/geo.png"
                      />
                      <span
                        style="
                          margin: 0 5px;
                          padding-right: 5px;
                          white-space: nowrap;
                        "
                        v-text="d.adresse"
                      ></span>
                      <span
                        style="
                          height: 5px;
                          border: 1px solid rgb(255, 143, 31);
                          font-size: 9px;
                          margin: 0px 5px;
                        "
                      ></span>
                      <span style="white-space: nowrap" v-text="d.cp"></span>
                    </p>
                  </td>
                </template>
              </tr>
            </table>
          </td>
        </tr>
        <tr>
          <td height="13"></td>
        </tr>
        <tr>
          <td>
            <table
              cellspacing="10"
              cellpadding="10"
              style="
                margin-left: 150px;
                margin-top: 0;
                color: rgb(131, 129, 138);
                border-spacing: 0px;
              "
            >
              <tbody>
                <tr style="line-height: 13px">
                  <td valign="middle" style="vertical-align: middle">
                    <a
                      href="https://www.outsourcia.com/actualites"
                      style="
                        text-decoration: none;
                        color: rgb(131, 129, 138);
                        margin: 0 2px 0 0px;
                      "
                      ><img
                        height="13"
                        alt="newsletter"
                        src="https://outsourcia-signature.netlify.app/assets/icons/newsletter.png"
                    /></a>
                  </td>
                  <td
                    valign="middle"
                    style="vertical-align: middle; padding-left: 5px"
                  >
                    <a
                      href="https://www.outsourcia.com/actualites"
                      style="text-decoration: none; color: rgb(131, 129, 138)"
                      >NEWSLETTER</a
                    >
                  </td>
                  <td valign="middle" style="vertical-align: middle">
                    <a
                      href="https://www.outsourcia.com/"
                      style="
                        text-decoration: none;
                        color: rgb(131, 129, 138);
                        margin: 0 2px 0 15px;
                      "
                      ><img
                        height="13"
                        alt="play"
                        src="https://outsourcia-signature.netlify.app/assets/icons/play.png"
                    /></a>
                  </td>
                  <td
                    valign="middle"
                    style="vertical-align: middle; padding-left: 5px"
                  >
                    <a
                      href="https://www.outsourcia.com/"
                      style="text-decoration: none; color: rgb(131, 129, 138)"
                      >VIDEO</a
                    >
                  </td>
                  <td valign="middle" style="vertical-align: middle">
                    <a
                      href="https://www.linkedin.com/company/groupe-outsourcia/"
                      style="
                        text-decoration: none;
                        color: rgb(131, 129, 138);
                        margin: 0 2px 0 15px;
                      "
                      ><img
                        height="13"
                        alt="linkedin"
                        src="https://outsourcia-signature.netlify.app/assets/icons/linkedin.png"
                    /></a>
                  </td>
                  <td
                    valign="middle"
                    style="vertical-align: middle; padding-left: 5px"
                  >
                    <a
                      href="https://www.linkedin.com/company/groupe-outsourcia/"
                      style="text-decoration: none; color: rgb(131, 129, 138)"
                      >LINKEDIN</a
                    >
                  </td>
                  <td valign="middle" style="vertical-align: middle">
                    <a
                      href="https://www.outsourcia.com/blog"
                      style="
                        text-decoration: none;
                        color: rgb(131, 129, 138);
                        margin: 0 2px 0 15px;
                      "
                      ><img
                        height="13"
                        src="https://outsourcia-signature.netlify.app/assets/icons/blog.png"
                    /></a>
                  </td>
                  <td
                    valign="middle"
                    style="vertical-align: bottom; padding-left: 5px"
                  >
                    <a
                      href="https://www.outsourcia.com/blog"
                      style="text-decoration: none; color: rgb(131, 129, 138)"
                      >BLOG</a
                    >
                  </td>
                </tr>
              </tbody>
            </table>
          </td>
        </tr>

        <tr v-if="data.consentement">
          <td style="padding: 0px 1px 0px 0px">
            <table
              style="max-width: 600px"
              cellspacing="0"
              cellpadding="0"
              border="0"
            >
              <tr>
                <td
                  style="
                    padding: 24px 1px 0px 0px;
                    font-family: Verdana, Geneva, sans-serif;
                    font-size: 10px;
                    line-height: 13px;
                    color: rgb(136, 136, 136);
                  "
                >
                  <p
                    style="
                      font-family: Verdana, Geneva, sans-serif;
                      font-size: 10px;
                      line-height: 13px;
                      color: rgb(136, 136, 136);
                      margin: 1px;
                    "
                  >
                    ---<br />Le contenu de cet e-mail est confidentiel et
                    destiné au destinataire spécifié dans le message uniquement.
                    Il est strictement interdit de partager toute partie de ce
                    message avec un tiers, sans le consentement écrit de
                    l'expéditeur.<br />Si vous avez reçu ce message par erreur,
                    veuillez répondre à ce message et suivre sa suppression,
                    afin que nous puissions nous assurer qu'une telle erreur ne
                    se reproduise plus à l'avenir.<br /><br />The content of
                    this email is confidential and intended for the recipient
                    specified in message only. It is strictly forbidden to share
                    any part of this message with any third party, without a
                    written consent of the sender.<br />If you received this
                    message by mistake, please reply to this message and follow
                    with its deletion, so that we can ensure such a mistake does
                    not occur in the future.<br />---
                  </p>
                </td>
              </tr>
            </table>
          </td>
        </tr>
        <!---->
        <!---->
      </table>
    </div>
  </div>
</template>

<style>
body {
  margin: 0;
}
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  border: 0;
}

ol,
ul {
  list-style: none;
}
img {
  display: inline !important;
}
</style>
