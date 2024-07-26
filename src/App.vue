<template>
  <div class="overflow-hidden bg-[#f7f7f7] py-24 sm:py-32 h-full">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto grid max-w-2xl grid-cols-1 gap-x-8 gap-y-16 sm:gap-y-20 lg:mx-0 lg:max-w-none lg:grid-cols-2">
        <div class="lg:pr-8 lg:pt-4">
          <div class="lg:max-w-lg">
            <p class="mt-2 text-2xl font-bold tracking-tight text-gray-900">Glossary of Mortgage & Lending Terms</p>
            <p class="mt-6 text-base text-gray-600">Use this glossary of mortgage terms to better understand the overall mortgage process as well as any specific mortgage terms that may be unfamiliar to you.</p>
              <input v-model="search" type="search" id="search" class="mt-6 bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Search" required />
          </div>
        </div>
        <!--results-->
        <div class="p-6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
          <div v-if="!search || results.length === 0" class="flex items-center justify-center">
            <div class="grid gap-4 w-60">
              <div class="w-20 h-20 mx-auto bg-gray-50 rounded-full shadow-sm justify-center items-center inline-flex">
                <svg xmlns="http://www.w3.org/2000/svg" width="33" height="32" viewBox="0 0 33 32" fill="none">
                  <g id="File Search">
                    <path id="Vector" d="M19.9762 4V8C19.9762 8.61954 19.9762 8.92931 20.0274 9.18691C20.2379 10.2447 21.0648 11.0717 22.1226 11.2821C22.3802 11.3333 22.69 11.3333 23.3095 11.3333H27.3095M18.6429 19.3333L20.6429 21.3333M19.3095 28H13.9762C10.205 28 8.31934 28 7.14777 26.8284C5.9762 25.6569 5.9762 23.7712 5.9762 20V12C5.9762 8.22876 5.9762 6.34315 7.14777 5.17157C8.31934 4 10.205 4 13.9762 4H19.5812C20.7604 4 21.35 4 21.8711 4.23403C22.3922 4.46805 22.7839 4.90872 23.5674 5.79006L25.9624 8.48446C26.6284 9.23371 26.9614 9.60833 27.1355 10.0662C27.3095 10.524 27.3095 11.0253 27.3095 12.0277V20C27.3095 23.7712 27.3095 25.6569 26.138 26.8284C24.9664 28 23.0808 28 19.3095 28ZM19.3095 16.6667C19.3095 18.5076 17.8171 20 15.9762 20C14.1352 20 12.6429 18.5076 12.6429 16.6667C12.6429 14.8257 14.1352 13.3333 15.9762 13.3333C17.8171 13.3333 19.3095 14.8257 19.3095 16.6667Z" stroke="#4F46E5" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round" />
                  </g>
                </svg>
              </div>
              <div>
                <h2 class="text-center text-black text-base font-semibold leading-relaxed pb-1">No results found</h2>
                <p class="text-center text-black text-sm font-normal leading-snug pb-4">Try changing your search to <br />see results</p>
              </div>
            </div>
          </div>
          <div v-else>
            <h2 class="text-base font-semibold leading-7">Definition for:</h2>
            <h2 class="text-lg font-bold text-indigo-600 uppercase">{{ search }}</h2>
            <p v-for="result in results" :key="result.short" class="mt-6 text-lg text-gray-600">
              {{ result.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import data from './assets/data.json';

export default {
  data() {
    return {
      search: '',
      data,
    };
  },
  computed: {
    results() {
      // Filter through the items and return items that match the search term.
      return this.data.filter(item => {
        return item.short.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  }
};
</script>