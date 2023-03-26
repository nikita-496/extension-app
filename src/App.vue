<script setup>
import { ref } from "vue";
import chromeIcon from "./components/ChromeIcon.vue";
import firefoxIcon from "./components/FirefoxIcon.vue";
import braveIcon from "./components/BraveIcon.vue";
import operaIcon from "./components/OperaIcon.vue";

const showChrome = ref(false);
const showFirefox = ref(false);
</script>

<template>
  <div class="wrapp">
    <img class="logo" src="./assets/bdns-64.svg" alt="bdns-logo" />
    <h1 class="intro">BDNS Wallet in your browser</h1>
    <p class="suggested">Download the extension to your favorite browser</p>
    <div class="links">
      <a
        href="/chrome/dist.zip"
        download
        @click="showChrome = true"
        class="button"
      >
        <chromeIcon />
      </a>
      <transition name="fade" appear>
        <div
          class="modal-overlay"
          v-if="showChrome"
          @click="showChrome = false"
        ></div>
      </transition>
      <transition name="pop" appear>
        <div class="modal" role="dialog" v-if="showChrome">
          <p>
            The newly downloaded directory containing the manifest must be added
            as an extension in developer mode
          </p>
          <ol>
            <li class="step">
              <p>
                Open the Extension Management page by navigating to
                <code class="code">chrome://extensions</code>.
              </p>
              <p>
                The Extension Management page can also be opened by clicking on
                the Chrome menu, hovering over More Tools then selecting
                Extensions.
              </p>
            </li>
            <li class="step">
              <p>
                Enable Developer Mode by clicking the toggle switch next to
                <strong> Developer mode </strong>.
              </p>
            </li>
            <li class="step">
              <p>
                Click the <strong>LOAD UNPACKED</strong> button and select the
                extension directory.
              </p>
            </li>
          </ol>

          <img
            class="image-example"
            src="https://wd.imgix.net/image/BrQidfK9jaQyIHwdw91aVpkPiib2/iYdLKFsJ1KSVGLhbLRvS.png?auto=format"
          />
        </div>
      </transition>

      <a
        href="/firefox/dist.zip"
        download
        @click="showFirefox = true"
        class="button"
      >
        <firefoxIcon />
      </a>
      <transition name="fade" appear>
        <div
          class="modal-overlay"
          v-if="showFirefox"
          @click="showFirefox = false"
        ></div>
      </transition>
      <transition name="pop" appear>
        <div class="modal" role="dialog" v-if="showFirefox">
          <p>
            The newly downloaded directory containing the manifest must be added
            as an extension in developer mode
          </p>
          <ol>
            <li class="step">
              <p>
                In Firefox: Open the
                <a
                  href="https://firefox-source-docs.mozilla.org/devtools-user/about_colon_debugging/index.html"
                  target="_blank"
                >
                  about:debugging
                </a>
                page, click the This Firefox option, click the Load Temporary
                Add-on button, then select any file in your extension's
                directory.
              </p>
            </li>
            <li class="step">
              <p>
                The extension now installs, and remains installed until you
                restart Firefox.
              </p>
            </li>
          </ol>
        </div>
      </transition>

      <a href="/chrome/dist.zip" download class="button">
        <braveIcon />
      </a>
      <a href="/chrome/dist.zip" download class="button">
        <operaIcon />
      </a>
    </div>
  </div>
</template>

<style scoped>
.wrapp {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.logo {
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #d3aa09aa);
}

.browser-list {
  margin-right: 45px;
  display: flex;
  list-style: none;
  gap: 0 10px;
  margin-top: 50px;
}
.browser-item {
  cursor: pointer;
}
.intro {
  color: #fff;
}
.suggested {
  color: #fff;
  font-weight: 300;
}
.modal {
  position: absolute;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  text-align: center;
  width: fit-content;
  height: fit-content;
  max-width: 50em;
  padding: 2rem;
  border-radius: 1rem;
  box-shadow: 0 5px 5px rgba(0, 0, 0, 0.2);
  background: rgba(231, 228, 228, 0.87);
  z-index: 999;
  transform: none;
}
.modal h1 {
  margin: 0 0 1rem;
}

.modal-overlay {
  content: "";
  position: absolute;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 998;
  background: #3d3d3d;
  opacity: 0.6;
  cursor: pointer;
}

/* ---------------------------------- */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.4s linear;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.pop-enter-active,
.pop-leave-active {
  transition: transform 0.4s cubic-bezier(0.5, 0, 0.5, 1), opacity 0.4s linear;
}

.pop-enter,
.pop-leave-to {
  opacity: 0;
  transform: scale(0.3) translateY(-50%);
}
.step {
  text-align: start;
}
.code {
  background: #c5c6c6;
  border: 1px solid #adaeae;
  border-radius: 3px;
}
.links {
  display: flex;
  gap: 0 10px;
}
</style>
