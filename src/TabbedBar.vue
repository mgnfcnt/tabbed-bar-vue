<template>
  <div class="navbar">
    <ul class="nav nav-pills nav-wizard">
      <li :class="[currentStep.step >= step.step ? 'active' : 'disabled']" v-for="step in steps" :key="step.step">
        <div class="nav-wedge" v-if="step.step > 1"/>
        <a class="hidden-xs" data-toggle="tab" :data-step="step.step">{{step.label}}</a>
        <a class="visible-xs" data-toggle="tab" :data-step="step.step">{{step.step}}.</a>
        <div class="nav-arrow" v-if="step.step < steps.length"/>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'tabbed-bar',
    props: {
      steps: {
        type: Array,
        required: true,
      },
      currentStep: {
        type: Object,
        required: true,
      },
    },
  };
</script>

<style lang="scss" scoped>
  li > a.hidden-xs {
    display: block !important;
  }

  li > a.visible-xs {
    display: none !important;
  }

  .nav-pills.nav-wizard > li {
    position: relative;
    overflow: visible;
    border-right: 10px solid #fff;
    border-left: 10px solid #fff;
  }

  .nav-pills.nav-wizard > li:first-child {
    border-left: 0;
  }

  .nav-pills.nav-wizard > li:first-child a {
    border-radius: 5px 0 0 5px;
  }

  .nav-pills.nav-wizard > li:last-child {
    border-right: 0;
  }

  .nav-pills.nav-wizard > li:last-child a {
    border-radius: 0 5px 5px 0;
  }

  .nav-pills.nav-wizard > li a {
    border-radius: 0;
    background-color: #eee;
    padding: 10px;
  }

  .nav-pills.nav-wizard > li .nav-arrow {
    position: absolute;
    top: 0;
    right: -20px;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 1.39em 0 1.39em 1.39em;
    border-color: transparent transparent transparent #eee;
    z-index: 150;
  }

  .nav-pills.nav-wizard > li .nav-wedge {
    position: absolute;
    top: 0;
    left: -1.2em;
    width: 0;
    height: 100%;
    border-style: solid;
    border-width: 1.39em 0 1.36em 1.39em;
    border-color: #eee #eee #eee transparent;
    z-index: 150;
  }

  .nav-pills.nav-wizard > li:hover .nav-arrow {
    border-color: transparent transparent transparent #aaa;
  }

  .nav-pills.nav-wizard > li:hover .nav-wedge {
    border-color: #aaa #aaa #aaa transparent;
  }

  .nav-pills.nav-wizard > li:hover a {
    background-color: #aaa;
    color: #fff;
  }

  .nav-pills.nav-wizard > li.active .nav-arrow {
    border-color: transparent transparent transparent #eb6a18;
  }

  .nav-pills.nav-wizard > li.active .nav-wedge {
    border-color: #eb6a18 #eb6a18 #eb6a18 transparent;
  }

  .nav-pills.nav-wizard > li.active a {
    background-color: #eb6a18;
  }
</style>
