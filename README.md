# Vue Auth0

A auth0-js V8 plugin for Vue 2.X

## Why?

I've seen my self in the need of create my own logins with Auth0 without the plugin they offer.

## Usage

Install the plugin like any other plugin. :)

~~~js
var Vue = require('vue');

Vue.use(require('vue-auth0'), {
  clientId: 'XXXXXXXXXXX',
  domain: 'myhost.auth0.com',
  callbackUrl: 'http://myhost/callback',
  audience: 'https://myhost.auth0.com/userinfo',
  redirectUri: 'https://myhost/callback',
})

~~~

### Manually using the auth0 instance.

Inside your components, you just need to access the `$auth0` object.

~~~js
export default {
    ready () {
        this.$auth0.login(username,password).then(() => {
            console.log(this.$auth0.profile)
        },error => {
            console.log(error)
        })
    },
    logout(){
        this.$auth0.logout();
    }
}
~~~


### After first login

Following data is saved on Local Storage:

- **expires_at:** Tokens time-to-live
- **id_token:** JWT that Auth0 returns
- **access_token:** Token for doing request about information and rules to Auth0
- **profile:** Profile information saved in a JSON


### Also accessible on components

- **this.$auth0.webAuth:** WebAuth object provided by Auth0
- **this.$auth0.profile:** Profile information
- **this.$auth9.options:** Options of the Initialization

