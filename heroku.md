Setting up _gu:who_ on Heroku
=============================

Follow the [Heroku Quick-Start guide](https://devcenter.heroku.com/articles/quickstart) to get your developement environment setup with Heroku.

Create a new Heroku app (eg `gu-who-nologo`), and push a clone of the [`gu:who` repository](https://github.com/guardian/gu-who) to the Heroku Git url to deploy the app (you'll see lots of dependencies downloaded, could take ~5 minutes):

```
$ git clone https://github.com/guardian/gu-who.git
$ cd gu-who
$ git push git@heroku.com:gu-who-nologo.git master
```

After Heroku deploy completes, your instance of _gu:who_ should be available:

https://gu-who-nologo.herokuapp.com/

At this point, pasting a valid GitHub access token into _gu:who_ and executing an audit will work, end to end. However, if you want to use the slightly more convenient 'Log In via GitHub` method [to authenticate via OAuth V2](https://developer.github.com/v3/oauth/), you'll need to register your instance of _gu:who_ as an application in your [GitHub settings](https://github.com/settings/applications/new). 

You now need to tell your Heroku instance the Client ID & Client Secret credentials, which will be visible in your GitHub application settings. The Heroku command is just:

```
$ heroku config:set --app gu-who-nologo GITHUB_APP_CLIENT_ID=0123456789abcdef GITHUB_APP_CLIENT_SECRET=0123456789abcdef01234567890abcdef
```

You've now got a fully configured Heroku _gu:who_ Heroku instance - but don't forget to setup the `people` Git repository in whatever GitHub organisation you'll be auditing as well!

