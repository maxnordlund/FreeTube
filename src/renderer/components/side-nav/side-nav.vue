<template>
  <ft-flex-box
    ref="sideNav"
    class="sideNav"
    :class="[{closed: !isOpen}, applyHiddenLabels]"
  >
    <div
      class="inner"
      :class="applyHiddenLabels"
    >
      <div
        class="navOption topNavOption mobileShow "
        role="button"
        tabindex="0"
        :title="$t('Subscriptions.Subscriptions')"
        @click="navigate('subscriptions')"
      >
        <div
          class="thumbnailContainer"
        >
          <font-awesome-icon
            icon="rss"
            class="navIcon"
            :class="applyNavIconExpand"
            fixed-width
          />
        </div>
        <p
          v-if="!hideText"
          class="navLabel"
        >
          {{ $t("Subscriptions.Subscriptions") }}
        </p>
      </div>
      <div
        v-if="!hideTrendingVideos"
        class="navOption mobileHidden"
        role="button"
        tabindex="0"
        :title="$t('Trending.Trending')"
        @click="navigate('trending')"
        @keypress="navigate('trending')"
      >
        <div
          class="thumbnailContainer"
        >
          <font-awesome-icon
            icon="fire"
            class="navIcon"
            :class="applyNavIconExpand"
            fixed-width
          />
        </div>
        <p
          v-if="!hideText"
          class="navLabel"
        >
          {{ $t("Trending.Trending") }}
        </p>
      </div>
      <div
        v-if="!hidePopularVideos"
        class="navOption mobileHidden"
        role="button"
        tabindex="0"
        :title="$t('Most Popular')"
        @click="navigate('popular')"
        @keypress="navigate('popular')"
      >
        <div
          class="thumbnailContainer"
        >
          <font-awesome-icon
            icon="users"
            class="navIcon"
            :class="applyNavIconExpand"
            fixed-width
          />
        </div>
        <p
          v-if="!hideText"
          class="navLabel"
        >
          {{ $t("Most Popular") }}
        </p>
      </div>
      <div
        v-if="!hidePlaylists"
        class="navOption mobileShow"
        role="button"
        tabindex="0"
        :title="$t('Playlists')"
        @click="navigate('userplaylists')"
        @keypress="navigate('userplaylists')"
      >
        <div
          class="thumbnailContainer"
        >
          <font-awesome-icon
            icon="bookmark"
            class="navIcon"
            :class="applyNavIconExpand"
            fixed-width
          />
        </div>
        <p
          v-if="!hideText"
          class="navLabel"
        >
          {{ $t("Playlists") }}
        </p>
      </div>
      <side-nav-more-options
        @navigate="navigate"
      />
      <div
        class="navOption mobileShow"
        role="button"
        tabindex="0"
        :title="$t('History.History')"
        @click="navigate('history')"
        @keypress="navigate('history')"
      >
        <div
          class="thumbnailContainer"
        >
          <font-awesome-icon
            icon="history"
            class="navIcon"
            :class="applyNavIconExpand"
            fixed-width
          />
        </div>
        <p
          v-if="!hideText"
          class="navLabel"
        >
          {{ $t("History.History") }}
        </p>
      </div>
      <hr>
      <div
        class="navOption mobileShow"
        role="button"
        tabindex="0"
        :title="$t('Settings.Settings')"
        @click="navigate('settings')"
        @keypress="navigate('settings')"
      >
        <div
          class="thumbnailContainer"
        >
          <font-awesome-icon
            icon="sliders-h"
            class="navIcon"
            :class="applyNavIconExpand"
            fixed-width
          />
        </div>
        <p
          v-if="!hideText"
          class="navLabel"
        >
          {{ $t('Settings.Settings') }}
        </p>
      </div>
      <div
        class="navOption mobileHidden"
        role="button"
        tabindex="0"
        :title="$t('About.About')"
        @click="navigate('about')"
        @keypress="navigate('about')"
      >
        <div
          class="thumbnailContainer"
        >
          <font-awesome-icon
            icon="info-circle"
            class="navIcon"
            :class="applyNavIconExpand"
            fixed-width
          />
        </div>
        <p
          v-if="!hideText"
          class="navLabel"
        >
          {{ $t("About.About") }}
        </p>
      </div>
      <hr>
      <div
        v-if="!hideActiveSubscriptions"
      >
        <div
          v-for="(channel, index) in activeSubscriptions"
          :key="index"
          class="navChannel mobileHidden"
          :title="channel.name"
          role="button"
          tabindex="0"
          @click="goToChannel(channel.id)"
          @keypress="goToChannel(channel.id)"
        >
          <div
            class="thumbnailContainer"
          >
            <img
              class="channelThumbnail"
              :src="channel.thumbnail"
            >
          </div>
          <p
            v-if="isOpen"
            class="navLabel"
          >
            {{ channel.name }}
          </p>
        </div>
      </div>
    </div>
  </ft-flex-box>
</template>

<script src="./side-nav.js" />
<style scoped src="./side-nav.css" />
