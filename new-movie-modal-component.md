# New Movie Modal Component

You have now created an amazing Netflix clone. How about adding more videos? This section, and the next, show you how to add a movie by uploading its title, banner, and trailer.

Start with adding an `UploadModal` component with the following content for the upload modal:

```markup
<template>
  <sweet-modal modal-theme="dark" overlay-theme="dark" ref="modal">
    <form @submit.prevent="handleUpload()" class="has-text-left">
      <div class="field">
        <label class="label has-text-white">Name</label>
        <div class="control">
          <input class="input" type="text" placeholder="Text input" v-model="title">
        </div>
      </div>
      <div class="field">
        <label class="label has-text-white">Upload Banner</label>
        <button class="button" @click="startUpload('banner')">Upload</button>
        <span class="has-text-white">{{banner}}</span>
      </div>
      <div class="field">
        <label class="label has-text-white">Upload Video</label>
        <button class="button" @click="startUpload('trailer')">Upload</button>
        <span class="has-text-white">{{trailer}}</span>
      </div>
      <button class="button is-danger">Submit</button>
    </form>
  </sweet-modal>
</template>
<script>
import { SweetModal, SweetModalTab } from 'sweet-modal-vue';
export default {
  components: {
    SweetModal,
    SweetModalTab
  }
};
</script>
```

The component contains a form with the following elements:

* An `input` class for `title`:

  ```markup
    <input class="input" type="text" placeholder="Text input" v-model="title">
  ```

* A `button` class for uploading `banner`:

  ```markup
    <button class="button" @click="startUpload('banner')">Upload</button>
  ```

* A `button` class for uploading `video`:

  ```markup
    <button class="button" @click="startUpload('trailer')">Upload</button>
  ```

* A `button` class for a **Submit** button:

  ```markup
    <button class="button is-danger">Submit</button>
  ```

* Two `span` tags to show the IDs of the uploaded items:

  ```markup
    <span class="has-text-white">{{banner}}</span>
  ```

To show a modal for an upload, leverage Vue's third-party library Sweet Modal.

