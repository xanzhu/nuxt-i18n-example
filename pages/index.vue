<script setup>
const { locales, locale, setLocale } = useI18n();
const switchLocalePath = useSwitchLocalePath();

const availableLocales = computed(() => {
  return locales.value.filter((i) => i.code !== locale.value);
});
</script>

<template>
  <div>
    <NuxtLink v-for="locale in availableLocales" @click.prevent.capture="setLocale(locale.code)" :key="locale.code"
      :to="switchLocalePath(locale.code)">
      {{ locale.name }}
    </NuxtLink>
  </div>

  {{ $t('welcome') }}
</template>