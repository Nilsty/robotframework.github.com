<template>
  <nav-mobile />
  <robocon-banner />
  <banner />
  <navbar class="nav-desktop" />
  <div class="container mb-xlarge">
    <!-- introduction -->
    <page-section
      title-id="introduction"
      :title="$t('introduction.title')">
      <div class="col-sm-12 col-lg-9 row">
        <div class="col-sm-12 col-lg-8 pr-small">
          <div v-html="$t('introduction.body')" id="intro-text" class="mb-small" />
          <!-- <company-carousel /> -->
        </div>
        <div class="col-lg-4 pt-2xsmall">
          <news />
        </div>
      </div>
    </page-section>
    <!-- getting started -->
    <page-section
      title-id="getting-started"
      :title="$t('gettingStarted.title')"
      :body="$t('gettingStarted.body')">
      <tab-box
        class="col-sm-12 col-lg-9 col-lg-offset-3"
        :tabs="$tm('gettingStarted.tabs')">
        <template v-slot:tab-1>
          <monaco-editor />
        </template>
        <!-- list of learning resouces on 3rd tab -->
        <template v-slot:tab-3>
            <div v-for="item in $tm('resourcesList.learning')" :key="item.name" class="mt-small mb-small">
              <a :href="item.href">
                {{ item.name }}
              </a>
              <div class="type-small" v-html="item.description" />
            </div>
        </template>
      </tab-box>
    </page-section>
    <!-- resources -->
    <page-section
      title-id="resources"
      :title="$t('resources.title')"
      :body="$t('resources.body')">
      <resource-box class="col-sm-12 col-lg-9 col-lg-offset-3" />
    </page-section>
    <!-- community -->
    <page-section
      title-id="community"
      :title="$t('community.title')"
      :body="$t('community.body')">
      <div class="col-sm-12 col-lg-9 col-lg-offset-3 row">
        <community-items />
        <button class="theme mt-medium" :class="$store.state.isMobile ? 'ml-xsmall' : ''">
          <router-link :to="{ name: 'CoC' }" class="type-no-underline">
            Code of Ethics
          </router-link>
        </button>
        <video-component videoId='2GDrtvz_1Ds' class="col-sm-12 mt-small" />
      </div>
    </page-section>
    <!-- development -->
    <page-section
      title-id="development"
      :title="$t('development.title')"
      :body="$t('development.body')">
      <sponsors class="col-sm-12 col-lg-9 col-lg-offset-3" />
      <milestones class="col-sm-12 col-lg-9 col-lg-offset-3 mt-medium" />
    </page-section>
  </div>
  <page-footer />
</template>

<script>
import { defineAsyncComponent } from 'vue'
import {
  RoboconBanner,
  Banner,
  PageFooter,
  Navbar,
  NavMobile,
  PageSection,
  News,
  CommunityItems,
  ResourceBox,
  TabBox,
  Sponsors,
  Milestones
} from 'Components'
import VideoComponent from 'Components/VideoComponent'

export default {
  name: 'App',
  components: {
    VideoComponent,
    RoboconBanner,
    Banner,
    PageFooter,
    Navbar,
    NavMobile,
    PageSection,
    News,
    CommunityItems,
    ResourceBox,
    TabBox,
    Sponsors,
    Milestones,
    MonacoEditor: defineAsyncComponent(() => import('Components/Editor.vue'))
  }
}
</script>

<style scoped>
@media screen and (max-width: 1024px) {
  .nav-desktop {
    display: none;
  }
}
</style>
