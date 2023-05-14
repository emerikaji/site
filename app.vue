<template>
  <div id="app">
    <full-page id="fullpage" ref="fullpage" :options="options">
      <div class="section bg-zinc-900 text-white">
        <div class="absolute top-0 left-0 mx-2 my-4 h-8 flex items-center space-x-2">
          <button v-on:click="popoverOpen = !popoverOpen">
            <svg viewBox="0 0 190 100" height="13">
              <rect width="190" height="20" fill="#FFFFFF"/>
              <rect y="40" width="190" height="20" fill="#FFFFFF"/>
              <rect y="80" width="190" height="20" fill="#FFFFFF"/>
            </svg>
          </button>
          <transition
          enter-active-class="duration-500 ease-out"
          enter-from-class="-translate-x-96 opacity-0"
          enter-to-class="translate-x-0 opacity-100"
          leave-active-class="duration-500 ease-out"
          leave-from-class="translate-x-0 opacity-100"
          leave-to-class="translate-x-96 opacity-0"
          >
            <ul v-if="popoverOpen" id="menu" class="z-50 flex items-center text-lg font-light text-white bg-black h-full">
              <li data-menuanchor="intro" class="w-28 h-full">
                <a v-on:click="popoverOpen = false" href="#intro" class="flex items-center justify-center hover:border-b-4 border-cyan-500 w-full h-full">Intro</a>
              </li>
              <li data-menuanchor="projects" class="w-28 h-full">
                <a v-on:click="popoverOpen = false" href="#projects" class="flex items-center justify-center hover:border-b-4 border-cyan-500 w-full h-full">Projects</a>
              </li>
              <li data-menuanchor="contact" class="w-28 h-full">
                <a v-on:click="popoverOpen = false" href="#contact" class="flex items-center justify-center hover:border-b-4 border-cyan-500 w-full h-full">Contact</a>
              </li>
            </ul>
          </transition>
        </div>
        <div class="flex w-screen h-screen">
          <div class="w-1/2 h-full flex items-center">
            <p class="font-mono text-8xl">Nishyda ~<br/>$ <span class="animate-blink">█</span></p>
          </div>
          <div class="w-1/2 h-full flex flex-col items-end">
            <div class="flex space-x-2 p-2">
              <nuxt-icon name="go" class="text-6xl"/>
              <nuxt-icon name="rust" class="text-5xl"/>
              <nuxt-icon name="cpp" filled class="text-5xl"/>
              <nuxt-icon name="php" class="text-6xl"/>
              <nuxt-icon name="ts" filled class="text-5xl"/>
              <nuxt-icon name="nuxt" class="text-6xl"/>
              <nuxt-icon name="next" class="text-6xl"/>
            </div>
            
          </div>
        </div>
      </div>
      <div class="section bg-zinc-900">
        <h3>Section 2</h3>
      </div>
      <div class="section bg-zinc-900">
        <h3>Section 3</h3>
      </div>
    </full-page>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      options: {
        afterLoad: this.afterLoad,
        scrollOverflow: true,
        scrollBar: false,
        menu: '#menu',
        navigation: true,
        anchors: ['intro', 'projects', 'contact']
      },
      popoverOpen: false
    }
  },
  methods: {
    afterLoad () {
      console.log('After load')
    }
  }
}
</script>