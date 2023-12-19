<script setup>
import { computed, ref } from "vue";
let data = ref({
  nom: "Nom",
  prenom: "Prénom",
  mail: "mail@outsourcia-group.com",
  fonction: "Fonction",
  consentement: true,
  pays: {
    FRANCE: {
      enabled: true,
      fixe: "+33 1 76 60 21 80",
      mobile: "+33 9 99 99 99 99",
      adresse: "23, rue Lavoisier",
      cp: "27 000 Evreux",
    },
    MAROC: {
      enabled: true,
      fixe: "+212 5 22 95 34 80",
      mobile: "+212 6 99 99 99 99",
      adresse: "217, Boulevard Anfa",
      cp: "21000 Casablanca",
    },
    TUNISIE: {
      enabled: false,
      fixe: "+216 36 40 02 00",
      mobile: "+216 9 99 99 99 99",
      adresse: "6 rue des entrepreneurs",
      cp: "2035 Charguia II",
    },
    MADAGASCAR: {
      enabled: false,
      fixe: "+261 20 22 572 21",
      mobile: "+261 9 99 99 99 99",
      adresse: "Enceinte Somalco, ZI Forello - Tanjombato",
      cp: "Antananarivo 102, Madagascar",
    },
  },
});

let isChrome =
  /Chrome/.test(navigator.userAgent) && /Google Inc/.test(navigator.vendor);

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
  <div v-if="!isChrome">
    <form
      class="flex flex-row gap-5 m-12"
      action=""
      method="POST"
      @submit.prevent="copy"
    >
      <div class="flex-1">
        <div class="relative mb-6">
          <div
            class="absolute inset-y-0 start-0 flex items-center ps-1 pointer-events-none"
          >
            <svg
              class="w-4 h-4 text-gray-800 dark:text-gray-900"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="currentColor"
              viewBox="0 0 20 16"
            >
              <path
                d="m10.036 8.278 9.258-7.79A1.979 1.979 0 0 0 18 0H2A1.987 1.987 0 0 0 .641.541l9.395 7.737Z"
              />
              <path
                d="M11.241 9.817c-.36.275-.801.425-1.255.427-.428 0-.845-.138-1.187-.395L0 2.6V14a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V2.5l-8.759 7.317Z"
              />
            </svg>
          </div>
          <input
            type="text"
            id="email"
            v-model="data.mail"
            class="block py-2.5 ps-6 pe-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-orange-800 focus:outline-none focus:ring-0 focus:border-orange-600 peer"
            placeholder=" "
          />
          <label
            for="email"
            class="absolute text-sm text-gray-800 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-placeholder-shown:start-6 peer-focus:start-0 peer-focus:text-orange-600 peer-focus:dark:text-orange-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto"
            >Adresse mail</label
          >
        </div>
        <div class="relative mb-6">
          <div
            class="absolute inset-y-0 start-0 flex items-center ps-1 pointer-events-none"
          >
            <svg
              class="w-4 h-4 text-gray-800 dark:text-white"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="currentColor"
              viewBox="0 0 20 16"
            >
              <path
                d="M18 0H2a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2ZM6.5 3a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5ZM3.014 13.021l.157-.625A3.427 3.427 0 0 1 6.5 9.571a3.426 3.426 0 0 1 3.322 2.805l.159.622-6.967.023ZM16 12h-3a1 1 0 0 1 0-2h3a1 1 0 0 1 0 2Zm0-3h-3a1 1 0 1 1 0-2h3a1 1 0 1 1 0 2Zm0-3h-3a1 1 0 1 1 0-2h3a1 1 0 1 1 0 2Z"
              />
            </svg>
          </div>
          <input
            type="text"
            id="nom"
            v-model="data.nom"
            class="block py-2.5 ps-6 pe-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-orange-500 focus:outline-none focus:ring-0 focus:border-orange-600 peer"
            placeholder=" "
          />
          <label
            for="nom"
            class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-placeholder-shown:start-6 peer-focus:start-0 peer-focus:text-orange-600 peer-focus:dark:text-orange-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto"
            >Nom</label
          >
        </div>
        <div class="relative mb-6">
          <div
            class="absolute inset-y-0 start-0 flex items-center ps-1 pointer-events-none"
          >
            <svg
              class="w-4 h-4 text-gray-800 dark:text-white"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="currentColor"
              viewBox="0 0 20 16"
            >
              <path
                d="M18 0H2a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2ZM6.5 3a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5ZM3.014 13.021l.157-.625A3.427 3.427 0 0 1 6.5 9.571a3.426 3.426 0 0 1 3.322 2.805l.159.622-6.967.023ZM16 12h-3a1 1 0 0 1 0-2h3a1 1 0 0 1 0 2Zm0-3h-3a1 1 0 1 1 0-2h3a1 1 0 1 1 0 2Zm0-3h-3a1 1 0 1 1 0-2h3a1 1 0 1 1 0 2Z"
              />
            </svg>
          </div>
          <input
            type="text"
            id="prenom"
            v-model="data.prenom"
            class="block py-2.5 ps-6 pe-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-orange-500 focus:outline-none focus:ring-0 focus:border-orange-600 peer"
            placeholder=" "
          />
          <label
            for="prenom"
            class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-placeholder-shown:start-6 peer-focus:start-0 peer-focus:text-orange-600 peer-focus:dark:text-orange-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto"
            >Pr&eacute;nom</label
          >
        </div>
        <div class="relative mb-6">
          <div
            class="absolute inset-y-0 start-0 flex items-center ps-1 pointer-events-none"
          >
            <svg
              class="w-4 h-4 text-gray-800 dark:text-white"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="currentColor"
              viewBox="0 0 20 16"
            >
              <path
                d="M18 0H2a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2ZM6.5 3a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5ZM3.014 13.021l.157-.625A3.427 3.427 0 0 1 6.5 9.571a3.426 3.426 0 0 1 3.322 2.805l.159.622-6.967.023ZM16 12h-3a1 1 0 0 1 0-2h3a1 1 0 0 1 0 2Zm0-3h-3a1 1 0 1 1 0-2h3a1 1 0 1 1 0 2Zm0-3h-3a1 1 0 1 1 0-2h3a1 1 0 1 1 0 2Z"
              />
            </svg>
          </div>
          <input
            type="text"
            id="fonction"
            v-model="data.fonction"
            class="block py-2.5 ps-6 pe-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-orange-500 focus:outline-none focus:ring-0 focus:border-orange-600 peer"
            placeholder=" "
          />
          <label
            for="fonction"
            class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-placeholder-shown:start-6 peer-focus:start-0 peer-focus:text-orange-600 peer-focus:dark:text-orange-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto"
            >Fonction</label
          >
        </div>
        <label class="relative inline-flex items-center mb-5 cursor-pointer">
          <input
            type="checkbox"
            v-model="data.consentement"
            value=""
            class="sr-only peer"
          />
          <div
            class="w-9 h-5 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-orange-300 dark:peer-focus:ring-orange-800 rounded-full peer dark:bg-gray-700 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-4 after:w-4 after:transition-all dark:border-gray-600 peer-checked:bg-orange-600"
          ></div>
          <span
            class="ms-3 text-sm font-medium text-gray-900 dark:text-gray-300"
            >Consentement</span
          >
        </label>
        <p>
          <button
            @click="copy"
            type="button"
            class="text-white bg-[#FF9119] hover:bg-[#FF9119]/80 focus:ring-4 focus:outline-none focus:ring-[#FF9119]/50 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center dark:hover:bg-[#FF9119]/80 dark:focus:ring-[#FF9119]/40 me-2 mb-2"
          >
            <svg
              class="w-4 h-4 text-white-800 dark:text-white"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 18 20"
            >
              <path
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="m7.708 2.292.706-.706A2 2 0 0 1 9.828 1h6.239A.97.97 0 0 1 17 2v12a.97.97 0 0 1-.933 1H15M6 5v4a1 1 0 0 1-1 1H1m11-4v12a.97.97 0 0 1-.933 1H1.933A.97.97 0 0 1 1 18V9.828a2 2 0 0 1 .586-1.414l2.828-2.828A2 2 0 0 1 5.828 5h5.239A.97.97 0 0 1 12 6Z"
              /></svg
            ><span class="ml-2">Copy</span>
          </button>
          <br />
          <a
            class="text-sm flex items-center justify-start ml-auto text-gray-500 transition-colors duration-200 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white"
            target="_blank"
            href="https://support.google.com/mail/answer/8395"
            >Ajouter une signature a Gmail<svg
              class="w-3.5 h-3.5 ml-2"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 14 10"
            >
              <path
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M1 5h12m0 0L9 1m4 4L9 9"
              ></path></svg
          ></a>
        </p>
      </div>
      <div class="grid grid-cols-2 gap-5">
        <div
          v-for="(d, pay) in data.pays"
          :key="pay"
          style="border-right: 1px solid #cdcdcd"
        >
          <label class="relative inline-flex items-center mb-5 cursor-pointer">
            <input
              type="checkbox"
              v-model="d.enabled"
              value=""
              class="sr-only peer"
            />
            <div
              class="w-9 h-5 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-orange-300 dark:peer-focus:ring-orange-800 rounded-full peer dark:bg-gray-700 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-4 after:w-4 after:transition-all dark:border-gray-600 peer-checked:bg-orange-600"
            ></div>
            <span
              class="ms-3 text-sm font-medium text-gray-900 dark:text-gray-300"
              v-text="pay"
            ></span>
          </label>
          <div class="my-5 flex gap-5">
            <div class="relative">
              <span
                class="absolute start-0 bottom-3 text-gray-500 dark:text-gray-400"
              >
                <svg
                  class="w-4 h-4 rtl:rotate-[270deg]"
                  aria-hidden="true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="currentColor"
                  viewBox="0 0 19 18"
                >
                  <path
                    d="M18 13.446a3.02 3.02 0 0 0-.946-1.985l-1.4-1.4a3.054 3.054 0 0 0-4.218 0l-.7.7a.983.983 0 0 1-1.39 0l-2.1-2.1a.983.983 0 0 1 0-1.389l.7-.7a2.98 2.98 0 0 0 0-4.217l-1.4-1.4a2.824 2.824 0 0 0-4.218 0c-3.619 3.619-3 8.229 1.752 12.979C6.785 16.639 9.45 18 11.912 18a7.175 7.175 0 0 0 5.139-2.325A2.9 2.9 0 0 0 18 13.446Z"
                  />
                </svg>
              </span>
              <input
                type="text"
                :id="pay + '_pay_fixe'"
                v-model="d.fixe"
                class="block py-2.5 ps-6 pe-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-orange-500 focus:outline-none focus:ring-0 focus:border-orange-600 peer"
                placeholder=" "
              />
              <label
                :for="pay + '_pay_fixe'"
                class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-placeholder-shown:start-6 peer-focus:start-0 peer-focus:text-orange-600 peer-focus:dark:text-orange-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto"
                >Fixe</label
              >
            </div>

            <div class="relative">
              <span
                class="absolute start-0 bottom-3 text-gray-500 dark:text-gray-400"
              >
                <svg
                  class="w-4 h-4 text-gray-800 dark:text-white"
                  aria-hidden="true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="currentColor"
                  viewBox="0 0 14 20"
                >
                  <path
                    d="M12 0H2a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2ZM7.5 17.5h-1a1 1 0 0 1 0-2h1a1 1 0 0 1 0 2ZM12 13H2V4h10v9Z"
                  />
                </svg>
              </span>
              <input
                type="text"
                :id="pay + '_pay_mobile'"
                v-model="d.mobile"
                class="block py-2.5 ps-6 pe-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-orange-500 focus:outline-none focus:ring-0 focus:border-orange-600 peer"
                placeholder=" "
              />
              <label
                :for="pay + '_pay_mobile'"
                class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-placeholder-shown:start-6 peer-focus:start-0 peer-focus:text-orange-600 peer-focus:dark:text-orange-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto"
                >Mobile</label
              >
            </div>
          </div>
          <div class="flex gap-5">
            <div class="relative">
              <span
                class="absolute start-0 bottom-3 text-gray-500 dark:text-gray-400"
              >
                <svg
                  class="w-4 h-4 text-gray-800 dark:text-white"
                  aria-hidden="true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="currentColor"
                  viewBox="0 0 16 20"
                >
                  <path
                    d="M8 0a7.992 7.992 0 0 0-6.583 12.535 1 1 0 0 0 .12.183l.12.146c.112.145.227.285.326.4l5.245 6.374a1 1 0 0 0 1.545-.003l5.092-6.205c.206-.222.4-.455.578-.7l.127-.155a.934.934 0 0 0 .122-.192A8.001 8.001 0 0 0 8 0Zm0 11a3 3 0 1 1 0-6 3 3 0 0 1 0 6Z"
                  />
                </svg>
              </span>
              <input
                type="text"
                :id="pay + '_pay_adresse'"
                v-model="d.adresse"
                class="block py-2.5 ps-6 pe-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-orange-500 focus:outline-none focus:ring-0 focus:border-orange-600 peer"
                placeholder=" "
              />
              <label
                :for="pay + '_pay_adresse'"
                class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-placeholder-shown:start-6 peer-focus:start-0 peer-focus:text-orange-600 peer-focus:dark:text-orange-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto"
                >Adresse</label
              >
            </div>

            <div class="relative">
              <span
                class="absolute start-0 bottom-3 text-gray-500 dark:text-gray-400"
              >
                <svg
                  class="w-4 h-4 text-gray-800 dark:text-white"
                  aria-hidden="true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="currentColor"
                  viewBox="0 0 14 20"
                >
                  <path
                    d="M7 0a7 7 0 0 0-1 13.92V19a1 1 0 1 0 2 0v-5.08A7 7 0 0 0 7 0Zm0 5.5A1.5 1.5 0 0 0 5.5 7a1 1 0 0 1-2 0A3.5 3.5 0 0 1 7 3.5a1 1 0 0 1 0 2Z"
                  />
                </svg>
              </span>
              <input
                type="text"
                :id="pay + '_pay_cp'"
                v-model="d.cp"
                class="block py-2.5 ps-6 pe-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-orange-500 focus:outline-none focus:ring-0 focus:border-orange-600 peer"
                placeholder=" "
              />
              <label
                :for="pay + '_pay_cp'"
                class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-placeholder-shown:start-6 peer-focus:start-0 peer-focus:text-orange-600 peer-focus:dark:text-orange-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto"
                >CP</label
              >
            </div>
          </div>
        </div>
      </div>
    </form>

    <div id="signature" class="mx-auto w-fit max-w-screen-lg overflow-x-auto">
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
                  <td style="padding-left: 40px; width: 100%">
                    <img
                      src="https://outsourcia-signature.netlify.app/assets/logo.svg"
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
                  <template v-if="d.enabled">
                    <td style="padding-right: 10px; padding-left: 10px">
                      <span
                        style="
                          color: #ff8f1f;
                          font-size: 12px;
                          font-weight: 500;
                        "
                        >{{ pay }}</span
                      >
                    </td>
                    <td
                      style="color: #83818a; font-size: 12px; font-weight: 600"
                    >
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
                    <td>
                      <p style="margin: 5px"></p>
                    </td>
                  </template>
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
                <tr style="line-height: 13px; font-size: 11px">
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
                    se reproduise plus à l'avenir.<br />---
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
  <div v-if="isChrome" class="w-full text-center p-12">
    Merci d'utiliser le navigateur
    <a class="text-orange-600" href="https://www.mozilla.org/fr/firefox/new/"
      >Firefox</a
    >
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
