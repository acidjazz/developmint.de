<template>
  <div class="flex flex-col flex-1 items-center my-24 mx-4 lg:m-8 lg:my-16 xl:my-0 lg:mx-18">
    <div class="w-full flex flex-col lg:flex-row items-center mb-4">
      <div class="my-4 flex-no-shrink">
        <img
          :alt="name"
          :src="require(`~/assets/img/about/${slug}.jpg`)"
          :srcset="`${require(`~/assets/img/about/${slug}@2x.jpg`)} 2x`"
          class="rounded-full border-4 border-solid border-grey-light shadow-lg"
          height="192"
          width="192"
        >
      </div>
      <div class="w-full lg:ml-8">
        <h2
          class="text-3xl py-3 border-b border-developmint text-center lg:text-left font-normal"
          v-text="name"
        />
        <div class="flex justify-around lg:justify-start mt-4">
          <a
            v-if="links.web"
            :href="links.web"
            class="no-underline group"
            @click="logClick('web')"
          >
            <GlobeIcon class="block w-6 h-6 mx-3 text-grey-darker group-hover:text-developmint transition-all fill-current" />
          </a>
          <a
            v-if="links.github"
            :href="links.github"
            class="no-underline group"
            @click="logClick('github')"
          >
            <GitHubIcon class="block w-6 h-6 mx-3 text-grey-darker group-hover:text-black transition-all fill-current" />
          </a>
          <a
            v-if="links.twitter"
            :href="links.twitter"
            class="no-underline group"
            @click="logClick('twitter')"
          >
            <TwitterIcon class="block w-6 h-6 mx-3 text-grey-darker group-hover:text-blue-light transition-all fill-current" />
          </a>
          <a
            v-if="links.linkedin"
            :href="links.linkedin"
            class="no-underline group"
            @click="logClick('linkedin')"
          >
            <LinkedInIcon class="block w-6 h-6 mx-3 text-grey-darker group-hover:text-blue-dark transition-all fill-current" />
          </a>
        </div>
      </div>
    </div>
    <!-- eslint-disable-next-line vue/no-v-html -->
    <p class="flex-grow text-justify leading-normal px-2" v-html="$t(`about.${slug}`)" />
  </div>
</template>

<script>
import logClick from '~/mixins/logClick'

export default {
  components: {
    GitHubIcon: () => import('~/assets/img/icons/github.svg'),
    GlobeIcon: () => import('~/assets/img/icons/team/globe.svg'),
    TwitterIcon: () => import('~/assets/img/icons/team/twitter.svg'),
    LinkedInIcon: () => import('~/assets/img/icons/team/linkedin.svg')
  },
  mixins: [logClick],
  props: {
    slug: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    links: {
      type: Object,
      default: () => ({})
    },
    odd: {
      type: Boolean,
      required: true
    }
  }
}
</script>
