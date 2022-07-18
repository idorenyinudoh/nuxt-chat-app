<template>
  <RobinChat v-bind="robinCreds" />
</template>

<script>
import { Robin } from 'robin.io-js'

export default {
  name: 'IndexPage',
  data () {
    return {
      robinCreds: {
        apiKey: 'NT-HfhLppTjlXOhWQCFsTMIUSVvDYHgnosJEgqA',
        userToken: 'random_tokenIDKwhat2SAY',
        userName: 'Idorenyin Udoh',
        keys: {
          userToken: 'user_token',
          profileImage: 'profile_image',
          userName: 'user_name'
        },
        users: [
          {
            user_token: 'random_tokenIDKwhat2SAY',
            profile_image: 'https://randomuser.me/api/portraits/men/34.jpg',
            user_name: 'Idorenyin Udoh'
          },
          {
            user_token: 'random_tokennIKwhat2SAY',
            profile_image: 'https://randomuser.me/api/portraits/men/34.jpg',
            user_name: 'Ekwueme Elvis'
          }
        ]
      }
    }
  },
  mounted () {
    this.createUserToken()
  },
  methods: {
    async createUserToken () {
      const robin = new Robin('NT-HfhLppTjlXOhWQCFsTMIUSVvDYHgnosJEgqA')
      const response = await robin.createUserToken({
        meta_data: {
          username: 'idorenyin'
        }
      })

      console.log(response)
    }
  }
}
</script>
