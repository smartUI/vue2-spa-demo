
<template>
  <list :error="error" :loading="loading" :listdata="listdata">
    <template slot="item" scope="props">
      <v-list-tile @click="">
        <v-list-tile-avatar>
          <span class="list-avatar-letter white--text red">
            {{ avatarLetter(props.item) }}
          </span>
        </v-list-tile-avatar>
        <v-list-tile-content>
          {{ props.item }}
        </v-list-tile-content>
      </v-list-tile>
    </template>
  </list>
</template>

<script>
import { listLoader, listGetter, avatarLetter } from '../utils'
import List from './List'

export default {
  name: 'blacklist',
  components: { List },
  props: ['room'],
  data () {
    return { loading: true, error: null }
  },
  computed: {
    listdata () {
      return listGetter.call(this, 'getBlacklist')
    }
  },
  methods: {
    avatarLetter
  },
  created () {
    listLoader.call(this, 'blacklist')
  }
}
</script>
