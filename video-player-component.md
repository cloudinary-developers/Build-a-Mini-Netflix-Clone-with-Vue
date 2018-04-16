# Video Player Component

Next, create a video-player component in the form of a file named `VideoPlayer.vue`, which plays the selected trailer or, in case none is selected, the default trailer.

Make the `VideoPlayer.vue` file read like this:

```markup
<template>
  <div class="trailer-bg">
      <video
        id="trailer"
        autoplay
        loop
        controls
        class="cld-video-player trailer-bg__video">
      </video>
      <div class="trailer-content">
        <h1 class="is-size-1  has-text-weight-bold">{{movie.title || 'Black Panther'}}</h1>
      </div>
  </div>
</template>

<script>
// We will add scripts in the
// next title
</script>

<style>
.trailer-bg {
  position: relative;
}
.trailer-bg__video {
  position: absolute;
  width: 100%;
  outline: none;
}
.trailer-content {
  position: absolute;
  top: 30%;
  left: 200px;
}
</style>
```

The above template relies on a `movie` object to show the content of the movie or that of the default. `movie` also renders a `video` tag to be attached to the source through the [Cloudinary API](https://cloudinary.com/documentation/video_player_api_reference?utm_source=Gitbook&utm_medium=VueJS&utm_content=Buid_Mini_Netflix_VueJS). Also created is a button for playing or pausing the trailer.

