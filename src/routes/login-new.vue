<template>
  <transition name="fade">
    <div class="login" :class="{ loading }">
      <div class="project-logo">
        <!-- <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 63" width="200" height="63"><path fill="#FFF" fill-rule="nonzero" d="M25.097 22.194h22.76c.247 1.192.357 2.629.357 4.173 0 4.986-1.402 11.192-5.855 15.582-4.343 4.444-9.895 6.829-17.262 6.829C11.463 48.778 0 37.83 0 24.389 0 10.948 11.463 0 25.097 0c7.531 0 12.92 2.927 16.932 6.775l-4.755 4.688c-2.886-2.683-6.817-4.77-12.177-4.77-9.951 0-17.73 7.913-17.73 17.723 0 9.81 7.779 17.723 17.73 17.723 6.432 0 10.115-2.548 12.48-4.878 1.924-1.924 3.188-4.661 3.683-8.4H25.097v-6.667zm42.76-5.343c8.85 0 16.072 6.518 16.072 15.52 0 8.949-7.223 15.52-16.072 15.52s-16.071-6.598-16.071-15.52c0-9.002 7.222-15.52 16.071-15.52zm0 24.832c4.791 0 8.929-3.836 8.929-9.312 0-5.53-4.138-9.312-8.929-9.312-4.79 0-8.928 3.783-8.928 9.312 0 5.476 4.137 9.312 8.928 9.312zM146 20.351v-2.693h6.679v28.135c0 11.55-6.983 16.288-15.234 16.288-7.783 0-12.447-5.088-14.213-9.234l6.127-2.477c1.104 2.557 3.78 5.573 8.086 5.573 5.27 0 8.555-3.204 8.555-9.181v-2.18h-.248c-1.573 1.884-4.61 3.553-8.445 3.553-8.003 0-14.986-6.865-14.986-15.642 0-8.83 6.983-15.642 14.986-15.642 3.836 0 6.872 1.669 8.445 3.5H146zm-8.054 21.332c4.761 0 8.51-3.889 8.483-9.26 0-5.396-3.722-9.364-8.483-9.364-4.815 0-8.482 3.889-8.482 9.312 0 5.344 3.667 9.312 8.482 9.312zm-34.375-24.832c8.85 0 16.072 6.518 16.072 15.52 0 8.949-7.223 15.52-16.072 15.52S87.5 41.293 87.5 32.371c0-9.002 7.222-15.52 16.071-15.52zm0 24.832c4.791 0 8.929-3.836 8.929-9.312 0-5.53-4.138-9.312-8.929-9.312-4.79 0-8.928 3.783-8.928 9.312 0 5.476 4.137 9.312 8.928 9.312zM158.036.887h7.143V47.89h-7.143V.887zm28.346 40.887c3.576 0 6.052-1.71 7.868-4.274l5.447 3.526c-1.76 2.51-5.997 6.865-13.315 6.865-9.079 0-15.846-6.812-15.846-15.52 0-9.243 6.85-15.52 15.076-15.52 8.28 0 12.352 6.41 13.673 9.883l.715 1.763-21.376 8.575c1.65 3.126 4.182 4.702 7.758 4.702zm-.404-19.602c-3.592 0-8.3 2.856-8.3 9.755l14.286-6.136c-.789-2.12-3.183-3.62-5.986-3.62z"/></svg> -->
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 209 40" width="209" height="40">
          <path
            fill="#FEFEFE"
            fill-rule="evenodd"
            d="M21.384 40l-5.086-16.19H6.666V40H0V0h18.982c5.315 0 9.59 4.288 9.59 9.545v4.342c0 3.771-2.281 6.97-5.422 8.457L28.584 40h-7.2zm.52-30.455c0-1.488-1.435-2.879-2.863-2.879H6.666v9.524h12.316c1.487 0 2.922-.817 2.922-2.303V9.545zM47.724 0h6.285l13.199 40h-7.255l-1.745-4.762H43.543L41.896 40h-7.312l13.14-40zm3.201 12.344l-5.372 16.229H56.18l-5.256-16.229zM95.115 0h6.665v40h-6.428L79.876 13.79V40h-6.668V0h6.28l15.626 26.267V0zm33.825 40h-9.6c-5.313 0-9.228-4.287-9.228-9.54V9.544c0-5.257 3.915-9.545 9.173-9.545h9.597c5.316 0 9.8 4.288 9.8 9.545v1.883h-6.663V9.545c0-1.488-1.65-2.879-3.079-2.879h-9.6c-1.485 0-2.56 1.39-2.56 2.879v20.914c0 1.484 1.075 2.875 2.505 2.875h9.597c1.488 0 3.137-1.39 3.137-2.875v-6.648h-7.622V16.19h14.286v14.27c0 5.253-4.485 9.54-9.743 9.54zm18.077-40h24.761v6.667h-18.095v9.523h18.095v7.621h-18.095v9.524h18.095V40h-24.761V0zm54.624 40l-5.086-16.19h-9.777V40h-6.668V0h19.133c5.312 0 9.44 4.288 9.44 9.545v4.342a9.33 9.33 0 0 1-5.35 8.457L208.84 40h-7.199zm.375-30.455c0-1.488-1.288-2.879-2.719-2.879h-12.52v9.524h12.466c1.485 0 2.773-.817 2.773-2.303V9.545z"
          />
        </svg>
      </div>

      <div class="container">
        <a href="https://directus.io" target="_blank">
          <img
            v-tooltip.right="{ classes: ['inverted'], content: version }"
            class="logo"
            alt=""
            src="../assets/logo-dark.svg"
          />
        </a>

        <v-install v-if="installing" :saving="saving" @install="install" />

        <form v-else @submit.prevent="processForm">
          <h1 v-if="loading">{{ loggedIn ? $t("fetching_data") : $t("signing_in") }}</h1>
          <h1 v-else-if="notInstalled">{{ $t("welcome") }}</h1>
          <h1 v-else>{{ resetMode ? $t("reset_password") : $t("sign_in") }}</h1>

          <label v-if="!selectOther" class="project-switcher">
            <select
              v-if="Object.keys(urls).length > 1 || allowOther"
              id="selectedUrl"
              v-model="selectedUrl"
              :disabled="loading"
              name="selectedUrl"
            >
              <option
                v-for="(name, u) in urls"
                :key="u"
                :value="u"
                :checked="u === url || u === url + '/'"
              >
                {{ name }}
              </option>
              <option v-if="allowOther" value="other">{{ $t("other") }}</option>
            </select>
            <div>
              <v-signal :strength="2" class="connection" />
              {{ urls[selectedUrl] || $t("choose_project") }}
              <v-icon
                v-if="Object.keys(urls).length > 1 || allowOther"
                size="24"
                class="icon"
                name="arrow_drop_down"
              />
            </div>
          </label>

          <label v-if="selectOther" class="project-other">
            <v-signal :strength="3" class="connection" />
            <input
              id="url"
              v-model="url"
              :disabled="loading"
              :class="{ 'has-value': url && url.length > 0 }"
              type="url"
              name="url"
              placeholder="Project URL"
            />
            <v-icon size="24" class="icon" name="close" />
          </label>

          <template v-if="notInstalled">
            <p class="install-copy">{{ $t("install_copy") }}</p>
            <button type="button" class="button" @click="installing = true">
              {{ $t("create_project") }}
            </button>
          </template>

          <template v-else>
            <input
              v-if="!missingOTP"
              id="email"
              v-model="email"
              autocomplete="email"
              :disabled="loading || exists === false"
              :class="{ 'has-value': email && email.length > 0 }"
              type="text"
              name="email"
              :placeholder="$t('email')"
            />

            <input
              v-if="!resetMode && !missingOTP"
              id="password"
              v-model="password"
              autocomplete="current-password"
              :disabled="loading || exists === false"
              :class="{ 'has-value': password && password.length > 0 }"
              type="password"
              name="password"
              :placeholder="$t('password')"
            />

            <input
              v-if="missingOTP"
              id="otp"
              v-model="otp"
              :disabled="loading || exists === false"
              :class="{ 'has-value': otp && otp.length > 0 }"
              type="text"
              name="otp"
              :placeholder="$t('otp')"
            />

            <div v-if="!resetMode" class="remember-forgot">
              <button v-if="!missingOTP" type="button" class="remember">
                <v-icon name="check_box_outline_blank" class="icon" />
                Remember Me
              </button>

              <button
                v-if="!missingOTP"
                type="button"
                class="forgot"
                @click.prevent="resetMode = !resetMode"
              >
                {{ resetMode ? $t("sign_in") : $t("forgot_password") }}
              </button>
            </div>

            <div class="login-register">
              <button class="button" type="submit" :disabled="disabled || loading">
                {{ resetMode ? $t("reset_password") : $t("sign_in") }}
              </button>

              <button class="button outline" :disabled="loading">
                Register
              </button>
            </div>

            <transition-group name="list" tag="div" class="stack">
              <ul key="third-party-auth" class="third-party-auth">
                <li v-for="provider in thirdPartyAuthProviders" :key="provider.name">
                  <a
                    v-tooltip.bottom="$helpers.formatTitle(provider.name)"
                    :href="url + 'auth/sso/' + provider.name"
                  >
                    <img :alt="provider.name" :src="provider.icon" />
                  </a>
                </li>
              </ul>
            </transition-group>
          </template>
        </form>

        <div class="notice">
          <span v-if="checkingExistence || gettingThirdPartyAuthProviders">
            <v-spinner
              key="spinner"
              class="spinner"
              :size="20"
              :line-size="2"
              line-fg-color="var(--gray)"
              line-bg-color="var(--blue-grey-100)"
            />
            Fetching Data
          </span>

          <span v-else-if="error || SSOerror" :class="errorType">
            <v-icon :name="errorType" class="icon" />
            {{ errorMessage }}
          </span>

          <span v-else>
            <v-icon
              v-if="thirdPartyAuthProviders && !thirdPartyAuthProviders.length"
              key="lock"
              :name="loggedIn ? 'lock_open' : 'lock_outline'"
              class="icon"
            />
            Not Authenticated
          </span>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import sdk from "@directus/sdk-js";
import { version } from "../../package.json";
import VSignal from "../components/signal.vue";

import VInstall from "../components/install.vue";

export default {
  name: "Login",
  components: {
    VInstall,
    VSignal
  },
  data() {
    return {
      selectedUrl: this.$store.state.auth.url + "/" + this.$store.state.auth.env + "/",

      url: null,
      email: null,
      password: null,
      otp: null,

      loading: false,
      loggedIn: false,
      error: null,
      SSOerror: null,

      exists: null,
      checkingExistence: false,
      thirdPartyAuthProviders: null,
      gettingThirdPartyAuthProviders: false,

      resetMode: false,

      installing: false,
      notInstalled: false,
      saving: false,

      missingOTP: false
    };
  },
  computed: {
    urls() {
      if (!window.__DirectusConfig__) return;
      return _.mapKeys(window.__DirectusConfig__.api, (val, key) =>
        key.endsWith("/") === false ? key + "/" : key
      );
    },
    allowOther() {
      if (!window.__DirectusConfig__) return;
      return window.__DirectusConfig__.allowOtherAPI;
    },
    version() {
      return `Directus v${version}`;
    },
    storeError() {
      return this.$store.state.auth.error;
    },
    errorType() {
      if (!this.error && !this.SSOerror) return;

      const errorCode = (this.error && this.error.code) || this.SSOerror;

      if (+errorCode >= 100 && +errorCode < 200) {
        if (+errorCode === 101 || +errorCode === 102) {
          return null;
        }

        return "warning";
      }
      return "error";
    },
    errorMessage() {
      if (!this.error && !this.SSOerror) return;

      const errorCode = (this.error && this.error.code) || this.SSOerror;

      if (this.localeMessages.errors && this.localeMessages.errors[errorCode] != null) {
        return this.$t(`errors[${errorCode}]`);
      }

      return this.$t("error_unknown");
    },
    localeMessages() {
      return this.$i18n.getLocaleMessage(this.$i18n.locale);
    },
    disabled() {
      if (this.resetMode) {
        if (this.email === null) return true;
        return this.email.length === 0;
      }

      if (this.email === null || this.password === null) return true;

      if (this.missingOTP) {
        if (this.otp === null) return true;
        else if (this.otp.length === 0) return true;
      }

      return this.email.length === 0 || this.password.length === 0;
    },
    selectOther() {
      return this.selectedUrl === "other";
    }
  },
  watch: {
    url() {
      this.exists = null;
      this.checkUrl();
    },
    selectedUrl(url) {
      if (url === "other") return;
      return (this.url = url);
    },
    exists(newVal) {
      if (newVal === true) {
        this.getThirdPartyAuthProviders();
      } else if (newVal === false) {
        this.error = { code: -1 };
      }
    },
    $route() {
      this.trySSOLogin();
    },
    storeError(error) {
      this.error = error;
    }
  },

  created() {
    this.checkUrl = _.debounce(this.checkUrl, 300);

    if (this.url) {
      this.checkUrl();
    }

    let lastUsedURL = this.$store.state.auth.url
      ? `${this.$store.state.auth.url}/${this.$store.state.auth.project}/`
      : Object.keys(window.__DirectusConfig__.api)[0];

    // Check if the last used URL is still a valid option before using it
    if (Object.keys(window.__DirectusConfig__.api).includes(lastUsedURL) === false) {
      lastUsedURL = null;
    }

    this.url = lastUsedURL || Object.keys(window.__DirectusConfig__.api)[0] || "";
    this.selectedUrl = this.url;

    if (this.url.endsWith("/") === false) this.url = this.url + "/";

    this.trySSOLogin();
  },
  beforeRouteEnter(to, from, next) {
    if (to.query.project) {
      return next(vm => {
        vm.selectedUrl = "other";
        vm.url = atob(to.query.project);
      });
    }
    return next();
  },
  methods: {
    processForm() {
      if (this.resetMode) {
        this.loading = true;

        this.$axios
          .post(this.url + "auth/password/request", {
            email: this.email
          })
          .then(() => {
            this.loading = false;
            this.$notify({
              title: this.$t("password_reset_sent", { email: this.email }),
              color: "green",
              iconMain: "check"
            });
          })
          .catch(error => {
            this.error = error;
            this.loading = false;
          });
      } else {
        const credentials = {
          url: this.url,
          email: this.email,
          password: this.password,
          otp: this.otp
        };

        this.loading = true;

        this.$store
          .dispatch("login", credentials)
          .then(() => {
            this.loggedIn = true;
            this.enterApp();
          })
          .catch(error => {
            if (error.code === 111) {
              this.missingOTP = true;
              this.error = null;
            } else if (error.code === 113) {
              this.$api.logout();
              return this.$router.push({
                path: "/2fa-activation",
                query: { temp_token: error.token }
              });
            }
            this.loading = false;
          });
      }
    },
    enterApp() {
      if (this.$route.query.redirect) {
        return this.$router.push(this.$route.query.redirect);
      }

      this.$api
        .getMe({ fields: "last_page" })
        .then(res => res.data.last_page)
        .then(lastPage => {
          if (lastPage == null || lastPage == "/logout" || lastPage == "/login") {
            lastPage = "/";
          }
          this.$router.push(lastPage);
        })
        .catch(error => {
          this.loading = false;
          this.$events.emit("error", {
            notify: this.$t("something_went_wrong_body"),
            error
          });
          this.$router.push("/");
        });
    },
    checkUrl() {
      if (!this.url) return;

      this.checkingExistence = true;
      this.exists = null;
      this.thirdPartyAuthProviders = null;
      this.error = null;
      this.notInstalled = false;

      const parts = this.url.split("/");
      parts.pop() || parts.pop();
      const newUrl = parts.join("/");

      this.$axios
        .get(newUrl + "/server/ping")
        .then(() => {
          this.exists = true;
          this.checkingExistence = false;
          this.error = null;
        })
        .catch(() => {
          this.exists = false;
          this.notInstalled = false;
          this.checkingExistence = false;
        });
    },
    getThirdPartyAuthProviders() {
      this.gettingThirdPartyAuthProviders = true;
      this.thirdPartyAuthProviders = null;

      const scopedAPI = new sdk();

      const parts = this.url.split("/");
      const env = parts.pop() || parts.pop();
      const newUrl = parts.join("/");

      scopedAPI.env = env;
      scopedAPI.url = newUrl;

      scopedAPI
        .getThirdPartyAuthProviders()
        .then(res => res.data)
        .then(thirdPartyAuthProviders => {
          this.thirdPartyAuthProviders = thirdPartyAuthProviders;
          this.gettingThirdPartyAuthProviders = false;
        })
        .catch(error => {
          if (error.code === 14) {
            this.notInstalled = true;
            this.exists = true;
          }

          this.gettingThirdPartyAuthProviders = false;
        });
    },
    trySSOLogin() {
      const queryParams = new URLSearchParams(window.location.search);
      if (queryParams.get("error")) {
        this.SSOerror = queryParams.get("code");

        const uri = window.location.toString();
        if (uri.indexOf("?") > 0) {
          const clean_uri = uri.substring(0, uri.indexOf("?"));
          window.history.replaceState({}, document.title, clean_uri);
        }

        return null;
      }

      if (queryParams.get("request_token") && queryParams.get("request_token").length > 0) {
        this.clearRequestToken();
        this.loading = true;
        this.$store
          .dispatch("loginSSO", queryParams.get("request_token"))
          .then(() => this.enterApp())
          .catch(error => {
            this.$events.emit("error", {
              notify: this.$t("something_went_wrong_body"),
              error
            });
            this.loading = false;
          });
      }
    },
    install(info) {
      const parts = this.url.split("/");
      parts.pop() || parts.pop();
      const newUrl = parts.join("/");
      this.saving = true;

      this.$axios
        .post(newUrl + "/projects", info)
        .then(() => {
          this.installing = false;
          this.exists = true;
          this.notInstalled = false;
          this.$notify({
            title: this.$t("api_installed"),
            color: "green",
            iconMain: "check"
          });
          this.saving = false;
        })
        .catch(error => {
          this.$events.emit("error", {
            notify: error.response.data.error.message,
            error
          });

          this.saving = false;
        });
    },
    clearRequestToken() {
      const url = window.location.href;
      const newUrl = url
        .replace(new RegExp("[?&]request_token=[^&#]*(#.*)?$"), "$1")
        .replace(new RegExp("([?&])request_token=[^&]*&"), "$1");

      history.replaceState({}, "Login | Directus", newUrl);
    }
  }
};
</script>

<style lang="scss" scoped>
.login {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  margin-left: 500px;
  background-color: var(--green); // Standard: --darkest-gray;
  background: url("/example-project-bg.jpg");
  background-size: cover;

  .project-logo {
    z-index: 2;
  }
}

.container {
  background-color: var(--white);
  max-width: 500px;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  padding: 40px 80px;
  box-shadow: 0 0 40px rgba(0, 0, 0, 0.25);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 3;
}

.logo {
  position: absolute;
  top: 40px;
  left: 80px;
  height: 40px;
  user-select: none;
  cursor: help;
}

.notice {
  position: absolute;
  bottom: 40px;
  left: 80px;
  user-select: none;
  pointer-events: none;
  color: var(--blue-grey-100);
  span {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    &.warning {
      color: var(--warning);
    }
    &.error {
      color: var(--danger);
    }
    .icon {
      transform: translateY(-1px);
      margin-right: 4px;
    }
    .spinner {
      margin-right: 8px;
    }
  }
}

form {
  width: 100%;
}

label {
  position: relative;
  text-transform: none;
  font-size: 16px;
  color: var(--light-gray);
  font-weight: 400;
}

h1 {
  color: var(--darker-gray);
  font-size: 48px;
  line-height: 48px;
  font-weight: 300;
  margin-bottom: 60px;
}

.project-switcher {
  border: 2px solid var(--blue-grey-100);
  width: 100%;
  padding: 20px 10px;
  margin-bottom: 32px;
  color: var(--gray);
  transition: border-color var(--fast) var(--transition);
  border-radius: var(--border-radius);

  &:hover {
    border-color: var(--gray);
  }
  select {
    position: absolute;
    width: calc(100% + 4px);
    height: calc(100% + 4px);
    opacity: 0;
    z-index: +1;
    top: -2px;
    right: -2px;
    bottom: -2px;
    left: -2px;
    font-size: 16px;
    cursor: pointer;
  }

  div {
    position: relative;
    transition: color var(--fast) var(--transition);
    padding-left: 32px;
    color: var(--darker-gray);
  }

  select:hover + div,
  select:focus + div {
    transition: none;
    cursor: pointer;
  }

  .icon {
    position: absolute;
    top: -2px;
    right: 0;
  }
  .connection {
    position: absolute;
    top: -3px;
    left: 0;
    width: 24px;
  }
}

.project-other {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 2px solid var(--blue-grey-100);
  width: 100%;
  height: 64px;
  padding: 20px 10px;
  margin-bottom: 32px;
  color: var(--gray);
  transition: border-color var(--fast) var(--transition);
  border-radius: var(--border-radius);

  &:hover {
    border-color: var(--gray);
  }

  input {
    width: calc(100% - 48px);
    height: calc(100% + 4px);
    z-index: +1;
    margin: 0;
    font-size: 16px;
    border: none;
  }

  .connection {
    width: 24px;
  }
  .icon {
    cursor: pointer;
    &:hover {
      color: var(--darker-gray);
    }
  }
}

input {
  position: relative;
  width: 100%;
  margin-bottom: 32px;
  border: 0;
  font-size: 16px;
  border: 2px solid var(--blue-grey-100);
  width: 100%;
  padding: 20px 10px;
  color: var(--darker-gray);
  transition: border-color var(--fast) var(--transition);
  border-radius: var(--border-radius);

  &::placeholder {
    color: var(--light-gray);
  }

  &:-webkit-autofill {
    color: var(--darker-gray) !important;
    -webkit-text-fill-color: var(--darker-gray);
    -webkit-box-shadow: 0 0 0px 1000px var(--white) inset;
  }

  &:hover:not([disabled]) {
    transition: none;
    border-color: var(--gray);
    &:focus {
      border-color: var(--darker-gray);
    }
  }

  &[disabled] {
    cursor: not-allowed;
  }

  &:focus {
    outline: 0;
    border-color: var(--darker-gray);

    &:-webkit-autofill {
      color: var(--darker-gray) !important;
      -webkit-text-fill-color: var(--darker-gray);
      -webkit-box-shadow: 0 0 0px 1000px var(--white) inset;
    }
  }
}

.remember-forgot {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 32px;
  button {
    text-decoration: none;
    transition: color var(--fast) var(--transition-out);
    color: var(--light-gray);

    &:hover,
    .user-is-tabbing &:focus {
      outline: 0;
      transition: none;
      color: var(--darkest-gray);
    }

    .icon {
      margin-top: -2px;
      margin-left: -3px;
    }
  }
}

.login-register {
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: max-height var(--slow) var(--transition-in);
}

.button {
  position: relative;
  background-color: var(--darkest-gray);
  border: 2px solid var(--darkest-gray);
  border-radius: var(--border-radius);
  color: var(--white);
  width: 100%;
  height: 60px;
  max-width: 154px;
  padding: 18px 10px;
  font-size: 16px;
  font-weight: 400;
  transition: background-color var(--fast) var(--transition);

  &[disabled] {
    cursor: not-allowed;
  }

  &:not([disabled]) {
    &:hover {
      background-color: var(--darkest-gray);
      border-color: var(--darkest-gray);
    }
  }

  &.outline {
    background-color: transparent;
    color: var(--darkest-gray);

    &[disabled] {
      background-color: transparent;
    }

    &:not([disabled]) {
      &:hover {
        background-color: transparent;
      }
    }
  }
}

.third-party-auth {
  padding: 0;
  list-style: none;
  display: flex;
  justify-content: space-around;

  a {
    display: block;
  }

  img {
    width: 21px;
    height: 21px;
    object-fit: contain;
  }
}

.list-enter-active {
  transition: var(--fast) var(--transition-in);
}

.list-leave-active {
  transition: var(--fast) var(--transition-out);
}

.list-enter,
.list-leave-to {
  opacity: 0;
}

.stack {
  position: relative;
  width: 100%;
  text-align: center;

  > * {
    position: absolute;
    left: 0;
    right: 0;
    margin: 0 auto;
  }
}

.close {
  position: absolute;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  z-index: 5;
  cursor: pointer;
  opacity: 0;
}

.fade-enter-active {
  opacity: 1;
  transition: var(--slow) var(--transition-in);

  form {
    transition: transform var(--slow) var(--transition-in);
  }
}

.fade-leave-active {
  transition: var(--slow) var(--transition-out);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 1000;

  form {
    transition: transform var(--slow) var(--transition-out);
  }
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.loading {
  pointer-events: none;
  user-select: none;

  input,
  .login-register {
    max-height: 0px;
    transition: var(--slow) var(--transition);
    opacity: 0;
    overflow: hidden;
  }

  .project-switcher i {
    display: none;
  }
}

@media (max-height: 800px) {
  h1 {
    margin-bottom: 32px;
  }

  .project-switcher,
  .remember-forgot,
  input {
    margin-bottom: 24px;
  }
}

.install-copy {
  margin: 32px 0;
  font-size: 16px;
  color: var(--light-gray);
  line-height: 26px;
  font-weight: 400;
}
</style>
