# Provision and Configure a Database

Next, create a database for storing movies. Each movie contains at least a title, a Cloudinary ID for a banner image, and another Cloudinary ID for a movie trailer. Follow the procedure below.

## Create an mLab Database

1. Go to the [mLab s](https://mlab.com) site, create an account, and open the [Create Wizard](https://mlab.com/create/wizard) page.
2. Click **SANDBOX **under **Plan Type**.
3. Click **Continue**.  


   ![](https://d2mxuefqeaa7sj.cloudfront.net/s_C4E0BB4A3CA481FA22D9AA6239D953F2B1D94D00408DB28F7AB567E3C6C4DB1A_1521565541349_Screen+Shot+2018-03-20+at+6.05.26+PM.png)

4. In the **AWS Region** dialog box, click a region and then click **Continue**.  


   ![](https://d2mxuefqeaa7sj.cloudfront.net/s_C4E0BB4A3CA481FA22D9AA6239D953F2B1D94D00408DB28F7AB567E3C6C4DB1A_1521565557555_Screen+Shot+2018-03-20+at+5.58.34+PM.png)

5. In the **Final Details** dialog box, type a name, for example, `miniflix`, in the **DATABASE NAME** text field and click **Continue**.  


   ![](https://d2mxuefqeaa7sj.cloudfront.net/s_C4E0BB4A3CA481FA22D9AA6239D953F2B1D94D00408DB28F7AB567E3C6C4DB1A_1521565577246_Screen+Shot+2018-03-20+at+5.59.10+PM.png)

6. Verify that the information displayed in the **Order Confirmation** dialog box is correct and then click **Submit Order**.

   ![](https://d2mxuefqeaa7sj.cloudfront.net/s_C4E0BB4A3CA481FA22D9AA6239D953F2B1D94D00408DB28F7AB567E3C6C4DB1A_1521565596684_Screen+Shot+2018-03-20+at+5.59.46+PM.png)

7. Create a user by returning to the home page \(Dashboard\), clicking the new database, and then clicking the **Users** tab.  

   ![](https://d2mxuefqeaa7sj.cloudfront.net/s_C4E0BB4A3CA481FA22D9AA6239D953F2B1D94D00408DB28F7AB567E3C6C4DB1A_1521565608850_Screen+Shot+2018-03-20+at+6.01.28+PM.png)

8. Click **Add database user** and, in the dialog box that is displayed, fill in the text fields. Click **CREATE**.

   ![](https://d2mxuefqeaa7sj.cloudfront.net/s_C4E0BB4A3CA481FA22D9AA6239D953F2B1D94D00408DB28F7AB567E3C6C4DB1A_1521565621135_Screen+Shot+2018-03-20+at+6.02.10+PM.png)

## Create a Database Middleware

Next, create a schema and model with the Mongoose library to interact with our database. To do this, use a middleware that connects and disconnects with the database every time you fetch or write to the database. Follow these steps:

1. Create a file named `db.js` with the following content in a folder called `middleware`:

   ```javascript
   // ./middleware/db.js
   var mongoose = require('mongoose');
   const MovieSchema = new mongoose.Schema({
      title: String,
      banner: String,
      trailer: String,
      created_at: Date,
      id: mongoose.Schema.ObjectId
   })
   module.exports = {
      // Connect/Disconnect middleware
      connectDisconnect: (req, res, next) => {
          // Create connection using Mongo Lab URL
          // available in Webtask context
   mongoose.createConnection(req.webtaskContext.secrets.MONGO_URL);
          // Create a mongoose model using the Schema
          req.movieModal = connection.model('Movie', MovieSchema);
          req.on('end', () => {
              // Disconnect when request
              // processing is completed
              mongoose.connection.close();
          })
          // Call next to move to
          // the next Express middleware
          next()
      },
   }
   ```

   `MovieSchema` is an instance on the Mongoose schema but configured to map to the objects you specified.

2. Create the middleware and export it as a function called `connectDisconnect`.
3. Create a database for the `mLab` database with `mongoose.createConnection`. Note that you are using the webtask context to fetch the URL from the environment so you need not hard-code your credentials.
4. Create a model with the connection and attach it to the request for access by the routes.
5. When the request ends, close the connection with `close`.

