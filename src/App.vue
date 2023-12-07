<script>
import sectionData from './assets/data.json'
export default {
  data() {
    return {
      isDesktop: window.innerWidth >= 768,
      activeTab: 0,
      activeAccordion: 0,
      sectionData: sectionData
    };
  },
  mounted() {
    window.addEventListener('resize', this.updateIsDesktop);
  },
  methods: {
    updateIsDesktop() {
      this.isDesktop = window.innerWidth >= 768;
    }
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.updateIsDesktop);
  }
};
</script>

<template>
  <div>
    <div class="tabs" v-if="isDesktop">
      <div class="tabs__container" >
        <div class="tabs__title">
          <button v-for="(section, index) in sectionData" :key="index" @click="activeTab = index" :class="{ active: activeTab === index }">{{ section.title }}</button>
        </div>

        <div class="tabs__content">
          <div v-for="(section, index) in sectionData" :key="index" class="section-content" v-show="activeTab === index">
            {{ section.content }}
          </div>
        </div>
      </div>
    </div>

    <div class="accordion" v-else>
      <div class="accordion__container" >
        <button v-for="(section, index) in sectionData" :key="index" @click="activeAccordion = index" :class="{ active: activeAccordion === index }">{{ section.title }}</button>
        
        <div v-for="(section, index) in sectionData" :key="index" class="accordion__content" v-show="activeAccordion === index">
          {{ section.content }}
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.accordion {
  &__container {
    display: flex;
    flex-direction: column;
  }
  &__title button {
    width: 200px;
  }
  
  &__content.active {
    display: block;
  }
}
@media (min-width: 1024px) {
  .tabs {
    &__container {
      display: flex;
      flex-direction: column;
    }

    &__title button {
      background-color: #fff;
      color: #000;
      padding: 5px
    }

    &__title button.active {
      border-bottom: none;
    }
    
    &__content.active {
      display: block;
    }
  }

}
</style>
