<script setup>
import {computed, ref} from "vue";

const triggers = ref([true, true, true, true])
const activeParts = computed(() => triggers.value.reduce((sum, a) => sum + a, 0))

const toggle = (triggerIndex) => {
  if (activeParts.value !== 1 || (activeParts.value === 1 && !triggers.value[triggerIndex])) {
    triggers.value[triggerIndex] = !triggers.value[triggerIndex]
  }
}
</script>

<template>
  <div class="main-page">
    <div class="header">
      <div class="header__title">Invictus</div>
      <div class="header__author">By William Ernest Henley</div>
    </div>
    <div class="content">
      <div class="menu">
        <div class="trigger" :class="{active: triggers[0]}" @click="() => toggle(0)"/>
        <div class="trigger" :class="{active: triggers[1]}" @click="() => toggle(1)"/>
        <div class="trigger" :class="{active: triggers[2]}" @click="() => toggle(2)"/>
        <div class="trigger" :class="{active: triggers[3]}" @click="() => toggle(3)"/>
      </div>
      <div class="text">
        <div class="part" v-if="triggers[0]">
          <span>Out of the night that covers me,</span><br>
          <span>Black as the pit from pole to pole,</span><br>
          <span>I thank whatever gods may be</span><br>
          <span>For my unconquerable soul.</span>
        </div>
        <div class="part" v-if="triggers[1]">
          <span>In the fell clutch of circumstance</span><br>
          <span>I have not winced nor cried aloud.</span><br>
          <span>Under the bludgeonings of chance</span><br>
          <span>My head is bloody, but unbowed.</span>
        </div>
        <div class="part" v-if="triggers[2]">
          <span>Beyond this place of wrath and tears</span><br>
          <span>Looms but the Horror of the shade,</span><br>
          <span>And yet the menace of the years</span><br>
          <span>Finds and shall find me unafraid.</span>
        </div>
        <div class="part" v-if="triggers[3]">
          <span> It matters not how strait the gate,</span><br>
          <span> How charged with punishments the scroll,</span><br>
          <span> I am the master of my fate,</span><br>
          <span> I am the captain of my soul.</span>
        </div>
      </div>
      <div class="right-area"/>
    </div>

  </div>
</template>

<style scoped lang="scss">
@import 'src/assets/scss/variables';

.main-page {
  padding: 1em 0;
}

.header {
  display: flex;
  justify-content: center;
  align-items: baseline;
  margin-bottom: 0.6em;

  @media (max-width: $bp-small) {
    flex-direction: column;
    text-align: center;
    align-items: normal;
  }

  &__title {
    margin-left: 5em;
    font-size: 2em;

    @media (max-width: $bp-small) {
      margin-left: 0;
    }
  }

  &__author {
    margin-left: 3em;
    font-size: 0.9em;
    font-weight: 500;

    @media (max-width: $bp-small) {
      margin-left: 0;
    }
  }
}

.content {
  display: flex;
}

.menu {
  display: flex;
  gap: 1em;
  margin: 0.3em 1em 0 0;

  @media (max-width: $bp-small) {
    flex-direction: column;
    margin: 0 1em 0 0;
  }
}

.trigger {
  border: 0.05em solid $black;
  width: 1em;
  height: 1em;
  cursor: pointer;

  &.active {
    background-color: $black;
  }
}

.text {
  width: 25em;
  font-size: 1em;

  @media (max-width: $bp-small) {
    width: calc(100vw - 6em);
  }

  .part {
    margin-bottom: 1em;
  }

  span:nth-child(4n+3) {
    display: inline-block;
    margin-left: 2em;

    @media (max-width: $bp-small) {
      margin-left: 0;
    }
  }
}

.right-area {
  width: 4em;

  @media (max-width: $bp-small) {
    width: 0;
  }
}

</style>
