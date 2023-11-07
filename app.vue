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
              <li v-if="!french" data-menuanchor="projects" class="w-28 h-full">
                <a v-on:click="popoverOpen = false" href="#projects" class="flex items-center justify-center hover:border-b-4 border-cyan-500 w-full h-full">Projects</a>
              </li>
              <li v-if="french" data-menuanchor="projects" class="w-28 h-full">
                <a v-on:click="popoverOpen = false" href="#projects" class="flex items-center justify-center hover:border-b-4 border-cyan-500 w-full h-full">Projets</a>
              </li>
              <li data-menuanchor="contact" class="w-28 h-full">
                <a v-on:click="popoverOpen = false" href="#contact" class="flex items-center justify-center hover:border-b-4 border-cyan-500 w-full h-full">Contact</a>
              </li>
              <li v-if="!french" data-menuanchor="toggle" class="w-32 h-full">
                <a v-on:click="popoverOpen = false; french = true" href="#" class="flex items-center justify-center hover:border-b-4 border-cyan-500 w-full h-full">Site français</a>
              </li>
              <li v-if="french" data-menuanchor="toggle" class="w-32 h-full">
                <a v-on:click="popoverOpen = false; french = false" href="#" class="flex items-center justify-center hover:border-b-4 border-cyan-500 w-full h-full">English website</a>
              </li>
            </ul>
          </transition>
        </div>
        <div class="flex w-screen h-screen">
          <div class="w-fit h-full flex flex-col justify-center whitespace-nowrap space-y-16 overflow-y-clip overflow-x-visible">
            <p class="font-mono text-8xl text-zinc-600">DevOps|Game<br />dev|WebApps</p>
            <p class="font-mono text-8xl">┌[Emerik ~]<br />└─ $<span class="animate-blink">█</span></p>
            <p class="font-mono text-8xl text-zinc-600">Android|Scr<br />ipting|UX/U</p>
          </div>
          <div style="background-image: url('servers.jpg')" class="w-full h-full bg-cover">
            <div class="w-full h-full flex flex-col justify-center items-end space-y-2 pt-2 pr-14 backdrop-blur-sm backdrop-brightness-50">
              <img src="/go.png" class="w-14"/>
              <img src="/rust.png" class="w-14"/>
              <img src="/cpp.png" class="w-14"/>
              <img src="/php.png" class="w-14"/>
              <img src="/ts.png" class="w-14"/>
              <nuxt-icon name="nuxt" class="flex items-center text-6xl h-6"/>
              <nuxt-icon name="next" class="flex items-center text-6xl h-6"/>
            </div>
          </div>
        </div>
      </div>
      <div class="section bg-zinc-600 text-white">
        <div class="w-screen h-screen flex items-center justify-center space-x-12">
          <div onclick="location.href='https://github.com/emerikaji/nbase';" class="flex flex-col aspect-[1/2] h-3/4 bg-zinc-900 shadow-zinc-800 hover:shadow-zinc-800 shadow-lg hover:shadow-xl rounded-lg transition hover:scale-105 overflow-hidden hover:cursor-pointer">
            <img src="/nbase.png" class="object-cover h-1/2"/>
            <div class="h-1/2 p-2">
              <p class="font-bold text-5xl mt-2">nBase</p>
              <p v-if="!french" class="mt-2 text-xl">Key/value store with miniLZO compression. Developed in Rust and features a simple terminal utility.</p>
              <p v-if="french" class="mt-2 text-xl">BDD clé/valeur avec compression miniLZO. Développé en Rust, utilisable en ligne de commande.</p>
            </div>
          </div>

          <div onclick="location.href='https://github.com/emerikaji/site';" class="flex flex-col aspect-[1/2] h-3/4 bg-zinc-900 shadow-zinc-800 hover:shadow-zinc-800 shadow-lg hover:shadow-xl rounded-lg transition hover:scale-105 overflow-hidden hover:cursor-pointer">
            <img src="" class="object-cover h-1/2"/>
            <div class="h-1/2 p-2">
              <p v-if="!french" class="font-bold text-5xl mt-2">Website</p>
              <p v-if="french" class="font-bold text-5xl mt-2">Site</p>
              <p v-if="!french" class="mt-2 text-xl">This website uses Nuxt.js, Fullpage.js and Tailwind. It is hosted with the help of Traefik and Docker Compose.</p>
              <p v-if="french" class="mt-2 text-xl">Ce site utilise Nuxt.js, Fullpage.js et Tailwind, et est déployé à l'aide de Traefik et Docker Compose.</p>
            </div>
          </div>
        </div>
      </div>
      <div class="section bg-zinc-900 text-white">
        <div class="w-screen h-screen flex">
          <p class="text-8xl">Contact</p>
          <div>
            
          </div>
          <div>

          </div>
        </div>
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
      popoverOpen: false,
      french: false
    }
  },
  methods: {
    afterLoad () {
      console.log('After load')
    }
  }
}
</script>