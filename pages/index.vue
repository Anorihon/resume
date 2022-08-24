<template>
  <main>
    <div class="content">
      <h1>Vladimir Mishchenko</h1>
      <h2>Software Developer</h2>
      <img
        src="~assets/img/avatar.jpg"
        alt="Avatar"
        class="avatar"
        draggable="false"
      >
      <section id="about-me">
        <h3>About me</h3>
        <div class="text">
          <p>My main frontend stack is - vanilla JS, Vue/Nuxt, SCSS, Webpack</p>
          <p>Except Photoshop I am familiar with Sketch and Figma</p>
          <p>I have hobby - game development. And that is why i get practice on different languages and tools, like Unity3d (C#), Godot (gdscript looks like Python), Phaser etc</p>
        </div>

        <ul id="contacts">
          <li class="contact">
            <div class="title">
              Phone:
            </div>
            <a href="tel:+380677471236">+38 067 747 1236</a>
          </li>
          <li class="contact">
            <div class="title">
              Email:
            </div>
            <a href="mailto:mrsign002@gmail.com">mrsign002@gmail.com</a>
          </li>
          <li class="contact">
            <div class="title">
              Telegram:
            </div>
            <a href="https://t.me/Anorihon">Write me</a>
          </li>
          <li class="contact">
            <div class="title">
              Website:
            </div>
            <a href="https://anorihon.com" target="_blank">anorihon.com</a>
          </li>
        </ul>

        <ul id="skills" class="box">
          <skill-component title="JavaScript" :progress="100" />
          <skill-component title="Vue" :progress="100" />
          <skill-component title="Nuxt" :progress="80" />
          <skill-component title="Angular" :progress="80" />
          <skill-component title="React" :progress="50" />
          <skill-component title="TypeScript" :progress="80" />
          <skill-component title="Phaser" :progress="85" />
          <skill-component title="Wordpress" :progress="100" />
          <skill-component title="PHP" :progress="60" />
          <skill-component title="С#" :progress="60" />
          <skill-component title="Git" :progress="100" />
          <skill-component title="SCSS" :progress="100" />
        </ul>
      </section>
    </div>
    <aside class="sidebar">
      <div id="experience" class="box">
        <h3>Experience</h3>
        <ul class="timeline">
          <work-place
            company="Bo-Co"
            position="Software developer"
            :start-date="new Date(Date.parse('Jul 2012'))"
            :finish-date="new Date(Date.parse('Apr 2013'))"
          >
            <p>I developed and maintained websites</p>
            <p>Supported about 40 sites, most are written in Wordpress, Joomla, Magic CMS (company's engine), a few in pure PHP</p>
            <p>For some sites I made regular and flash banners</p>
          </work-place>
        </ul>
      </div>
    </aside>
  </main>
</template>

<script lang="ts">
import Vue from 'vue'
import SkillComponent from '~/components/Skill.vue'

export default Vue.extend({
  name: 'IndexPage',
  components: { SkillComponent }
})
</script>

<style src="assets/styles/resume.scss" lang="scss"></style>
