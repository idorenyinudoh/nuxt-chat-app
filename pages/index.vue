<template>
  <!-- ... -->
  <RobinChat
    v-if="tokenIsReady"
    :api-key="apiKey"
    :user-token="users[0].user_token"
    user-name="Idorenyin Udoh"
    :keys="keys"
    :users="users"
  />
</template>

<script>
import { Robin } from 'robin.io-js'

export default {
  name: 'IndexPage',
  data () {
    return {
      tokenIsReady: false,
      apiKey: 'NT-HfhLppTjlXOhWQCFsTMIUSVvDYHgnosJEgqA',
      keys: {
        userToken: 'user_token',
        profileImage: 'profile_image',
        userName: 'user_name'
      },
      users: [
        {
          user_token: '',
          profile_image: '',
          user_name: 'idorenyin'
        },
        {
          user_token: '',
          profile_image: '',
          user_name: 'ayo'
        },
        {
          user_token: '',
          profile_image: '',
          user_name: 'elvis'
        },
        {
          user_token: '',
          profile_image: '',
          user_name: 'favour'
        },
        {
          user_token: '',
          profile_image: '',
          user_name: 'enoch'
        }
      ]
    }
  },
  created () {
    this.createTokens()
  },
  methods: {
    async createTokens () {
      const robin = new Robin(this.$config.robinApiKey, true)
      for (let i = 0; i < this.users.length; i++) {
        await robin.createUserToken({
          meta_data: {
            username: this.users[i].user_name
          }
        }).then((res) => {
          this.users[i].user_token = res.data.user_token
        })
      }
      this.tokenIsReady = true
    }
  }
}
</script>
