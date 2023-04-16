<script setup>
// import Versions from './components/Versions.vue'
import DataView from './components/DataView.vue'
import MessageBoard from './components/MessageBoard.vue'
// Kakao.init('a58f889b066015dd555af2bb7577af7e')
// console.log('kakao_initialized: ', Kakao.isInitialized())

</script>

<template>
  <!-- <Versions></Versions> -->

<!-- <svg class="hero-logo" viewBox="0 0 900 300">
                          <use xlink:href="./assets/icons.svg#electron" />
          </svg> -->
<h2 class="hero-text">비대면 Manager</h2>
<!-- <p class="hero-tagline">Please try pressing <code>F12</code> to open the devTool</p> -->

<!-- <div class="links">
    <div class="link-item">
      <a target="_blank" href="https://evite.netlify.app">Documentation</a>
    </div>
    <div class="link-item link-dot">•</div>
      <div class="link-item">
              <a target="_blank" href="https://github.com/alex8088/electron-vite">Getting Help</a>
                </div>
                  <div class="link-item link-dot">•</div>
                  <div class="link-item">
                                  <a target="_blank" href="https://github.com/alex8088/quick-start/tree/master/packages/create-electron">
                                    create-electron
                                  </a>
                                </div>
                              </div> -->

  <div class="features">
    <div class="feature-item">
      <article>
        <h2 class="title">Configuring</h2>
        <p class="detail">
          Config with <span>electron.vite.config.js</span> and refer to the
          <a target="_blank" href="https://evite.netlify.app/config/">config guide</a>.
        </p>
      </article>
    </div>
    <div class="feature-item">
      <article>
        <h2 class="title">HMR</h2>
        <p class="detail">
          Edit <span>src/renderer</span> files to test HMR. See
          <a target="_blank" href="https://evite.netlify.app/guide/hmr-in-renderer.html">docs</a>.
        </p>
      </article>
    </div>
    <div class="feature-item">
      <article>
        <h2 class="title">Hot Reloading</h2>
        <p class="detail">
          Run <span>'electron-vite dev --watch'</span> to enable. See
          <a target="_blank" href="https://evite.netlify.app/guide/hot-reloading.html">docs</a>.
        </p>
      </article>
    </div>
    <div class="feature-item">
      <article>
        <h2 class="title">Debugging</h2>
        <p class="detail">
          Check out <span>.vscode/launch.json</span>. See
          <a target="_blank" href="https://evite.netlify.app/guide/debugging.html">docs</a>.
        </p>
      </article>
    </div>
    <div class="feature-item">
      <article>
        <h2 class="title">Source Code Protection</h2>
        <p class="detail">
          Supported via built-in plugin <span>bytecodePlugin</span>. See
          <a target="_blank" href="https://evite.netlify.app/guide/source-code-protection.html">
            docs
          </a>
          .
        </p>
      </article>
    </div>
    <div class="feature-item">
      <article>
        <h2 class="title">Packaging</h2>
        <p class="detail">
          Use
          <a target="_blank" href="https://www.electron.build">electron-builder</a>
          and pre-configured to pack your app.
        </p>
      </article>
    </div>
  </div>
  <message-board></message-board>
  <data-view></data-view>
</template>

<style lang="less">
@import './assets/css/styles.less';
</style>
