# Sharing on Twitter

Finally, we can give users a chance to share the trailers they've just added on Twitter.

Install the Vue Social library:

```bash
npm install --save vue-social-sharing
```

Configure the library in `src/main.js`:

```javascript
const SocialSharing = require('vue-social-sharing');

Vue.use(SocialSharing);
```

Add the following to the nav bar items:

```markup
<a class="button navbar-item">
  <social-sharing 
    title="Build a Mini Netflix from scratch" 
    url="https://cloudinary.gitbooks.io/build-a-mini-netflix-clone-with-vue/content" inline-template>
    <div>
      <network network="twitter">
        Share
      </network>
    </div>
  </social-sharing>
</a>
```

