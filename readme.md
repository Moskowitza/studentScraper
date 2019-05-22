### Let's get deployable.

- Install `dotenv` node package (npm i dotenv)
- In the route of your directory create a `.env` file
- `.env` to your `.gitignore`
- In `.env` put `MONGODB_URI=mongodb://localhost/yourdatabasename`

In your server file make sure you have the following

- `require('dotenv').config();` as high up in the file as possible
- `const db = require('./models');` I'm ASSUMING you have an index.js file in your models folder exporting your modules
- `const PORT = process.env.PORT || 3000;` to handle running on heroku and locally
- `mongoose.connect(process.env.MONGODB_URI, { useNewUrlParser: true });` we'll always use _MONGODB_URI_ to as our reference since that's what heroku calls it.

From the Command line

- cd in to your project and run the following commands
- `heroku create`
- `git remote -v` see that you have new remotes for heroku
- `heroku addons:create mongolab`
- `heroku config:get MONGODB_URI` you should see a value for MONGODB_URI returned.

If all that seems to worked well, you can double check on heroku.com for your app, and in settings-> reveal config should show the same MONGODB_URI name

- `git add -A`
- `git commit -m 'ready to deploy'`
- `git push heroku master`
  if build succeeded
- `heroku open`
