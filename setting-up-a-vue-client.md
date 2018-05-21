# Setting Up a Vue Client

You have now completed the server tasks. Now build the client app in a different folder, written in Vue, which simplifies tasks, such as manipulation of the Document Object Model \(DOM\) and management of states.

## Install the Vue CLI

Just like the webtask CLI, the Vue CLI scaffolds a new Vue project without the hassle of configurations. Run this command line:

```bash
npm install @vue/cli -g
```

## Create a Vue Project

1. Create a Vue project with the CLI you just installed:

   ```bash
   vue create mini-netflix
   ```

![](https://d2mxuefqeaa7sj.cloudfront.net/s_C4E0BB4A3CA481FA22D9AA6239D953F2B1D94D00408DB28F7AB567E3C6C4DB1A_1521569426688_Screen+Shot+2018-03-19+at+12.16.20+PM.png)

2. Go to the `mini-netflix` folder created by the command in step 1:

   ```bash
   cd mini-netflix
   ```

3. Test-run the scaffold:

   ```bash
   npm run serve
   ```

![](https://d2mxuefqeaa7sj.cloudfront.net/s_C4E0BB4A3CA481FA22D9AA6239D953F2B1D94D00408DB28F7AB567E3C6C4DB1A_1521569882249_Screen+Shot+2018-03-20+at+7.17.15+PM.png)

## Set Up the Library Dependencies

Specify the libraries for the project by editing your `package.json` file to read like this:

```javascript
"dependencies": {
  "axios": "^0.18.0",
  "node-sass": "^4.7.2",
  "sass-loader": "^6.0.7",
  "sweet-modal-vue": "^2.0.0",
  "vue": "^2.5.13",
  "vue-social-sharing": "^2.3.3"
},
```

Afterwards, run `npm install` to download the libraries.

