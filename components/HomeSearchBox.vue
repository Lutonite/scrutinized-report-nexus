<script>
export default {
  props: {
    cache: {
      type: Object,
      default: () => ({})
    }
  },
  data() {
    return {
      lists: {
        names: this.cache.NAMES,
        reportDates: this.cache.REPORT_DATES,
        minAges: this.cache.MIN_AGES,
        maxAges: this.cache.MAX_AGES,
        heights: this.cache.HEIGHTS,
        weights: this.cache.WEIGHTS,
        genders: this.cache.GENDERS,
        hairColors: this.cache.HAIR_COLORS,
        eyeColors: this.cache.EYE_COLORS
      }
    };
  },
  computed: {
    reloadKeymap() {
      return {
        'ctrl+r': this.reload
      };
    },
    search() {
      return this.$store.state.search;
    }
  },
  methods: {
    reload(event) {
      event.preventDefault();
      event.stopPropagation();
      this.$vuetify.goTo(0).then(() => {
        this.$store.commit('resetSearch');
      });
    },
    blur(i) {
      console.log(this.$refs[0]);
      [0, 1, 2, 3, 4, 5, 6, 7, 8].filter(x => i !== x).forEach(j => {
        this.$refs[j].blur();
      });
    }
  }
};
</script>

<template>
  <VRow v-hotkey="reloadKeymap" align="center" justify="center" no-gutters="">
    <VCol cols="12">
      <VCard elevation="6">
        <VCardText>
          <form autocomplete="off">
            <VRow dense>
              <VCol cols="6">
                <AutocompleteInput
                  :ref="0"

                  :value="search.name"
                  label="Name Search (Alt+Q)"

                  shortcut="alt+q"
                  :items="lists.names"
                  :cache="cache"
                  @input="$store.commit('search', {key: 'name', value: $event})"
                  @blur-fields="blur(0)"
                />
              </VCol>
              <VCol cols="6">
                <AutocompleteInput
                  :ref="1"

                  :value="search.reportDate"
                  label="Report Date (Alt+E)"

                  shortcut="alt+e"
                  :items="lists.reportDates"
                  :cache="cache"
                  @input="$store.commit('search', {key: 'reportDate', value: $event})"
                  @blur-fields="blur(1)"
                />
              </VCol>
              <VCol cols="3">
                <AutocompleteInput
                  :ref="2"

                  :value="search.minAge"
                  label="Min Age (Alt+A)"

                  shortcut="alt+a"
                  :items="lists.minAges"
                  :cache="cache"
                  @input="$store.commit('search', {key: 'minAge', value: $event})"
                  @blur-fields="blur(2)"
                />
              </VCol>
              <VCol cols="3">
                <AutocompleteInput
                  :ref="3"

                  :value="search.maxAge"
                  label="Max Age (Alt+S)"

                  shortcut="alt+s"
                  :items="lists.maxAges"
                  :cache="cache"
                  @input="$store.commit('search', {key: 'maxAge', value: $event})"
                  @blur-fields="blur(3)"
                />
              </VCol>
              <VCol cols="3">
                <AutocompleteInput
                  :ref="4"

                  :value="search.height"
                  label="Height (Alt+D)"

                  shortcut="alt+d"
                  :items="lists.heights"
                  :cache="cache"
                  @input="$store.commit('search', {key: 'height', value: $event})"
                  @blur-fields="blur(4)"
                />
              </VCol>
              <VCol cols="3">
                <AutocompleteInput
                  :ref="5"

                  :value="search.weight"
                  label="Weight (Alt+F)"

                  shortcut="alt+f"
                  :items="lists.weights"
                  :cache="cache"
                  @input="$store.commit('search', {key: 'weight', value: $event})"
                  @blur-fields="blur(5)"
                />
              </VCol>
              <VCol cols="4">
                <AutocompleteInput
                  :ref="6"

                  :value="search.gender"
                  label="Gender (Alt+Y)"

                  shortcut="alt+y"
                  :items="lists.genders"
                  :cache="cache"
                  @input="$store.commit('search', {key: 'gender', value: $event})"
                  @blur-fields="blur(6)"
                />
              </VCol>
              <VCol cols="4">
                <AutocompleteInput
                  :ref="7"

                  :value="search.hairColor"
                  label="Hair Color (Alt+X)"

                  shortcut="alt+x"
                  :items="lists.hairColors"
                  :cache="cache"
                  @input="$store.commit('search', {key: 'hairColor', value: $event})"
                  @blur-fields="blur(7)"
                />
              </VCol>
              <VCol cols="4">
                <AutocompleteInput
                  :ref="8"

                  :value="search.eyeColor"
                  label="Eye Color (Alt+C)"

                  shortcut="alt+c"
                  :items="lists.eyeColors"
                  :cache="cache"
                  @input="$store.commit('search', {key: 'eyeColor', value: $event})"
                  @blur-fields="blur(8)"
                />
              </VCol>
            </VRow>
          </form>
        </VCardText>
      </VCard>
    </VCol>
  </VRow>
</template>
