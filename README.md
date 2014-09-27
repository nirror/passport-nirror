# Passport-Nirror
[Passport](http://passportjs.org/) strategy for authenticating with [Nirror](https://www.nirror.com/)
using the OAuth 2.0 API.

This module lets you authenticate using Nirror in your Node.js applications.
By plugging into Passport, Nirror authentication can be easily and
unobtrusively integrated into any application or framework that supports
[Connect](http://www.senchalabs.org/connect/)-style middleware, including
[Express](http://expressjs.com/).

## Install
    $ npm install passport-nirror

## Usage
### Configure Strategy

The Nirror authentication strategy authenticates users using a Nirror account
and OAuth 2.0 tokens.  The strategy requires a `verify` callback, which accepts
these credentials and calls `done` providing a user, as well as `options`
specifying a client ID, client secret, and callback URL.

    passport.use(new DropboxOAuth2Strategy({
        clientID: NIRROR_CLIENT_ID,
        clientSecret: NIRROR_CLIENT_SECRET,
        callbackURL: "https://www.example.net/auth/nirror/callback"
      },
      function(accessToken, refreshToken, profile, done) {
        User.findOrCreate({ providerId: profile.id }, function (err, user) {
          return done(err, user);
        });
      }
    ));

### Authenticate Requests
Use `passport.authenticate()`, specifying the `'nirror'` strategy, to
authenticate requests.

For example, as route middleware in an [Express](http://expressjs.com/)
application:

    app.get('/auth/nirror',
      passport.authenticate('nirror'));

    app.get('/auth/nirror/callback', 
      passport.authenticate('nirror', { failureRedirect: '/login' }),
      function(req, res) {
        // Successful authentication, redirect home.
        res.redirect('/');
      });

## Prior work
This strategy is based on Jared Hanson's GitHub strategy for passport: [Jared Hanson](http://github.com/jaredhanson)

## Credits and License
express-sslify is licensed under the MIT license.

Copyright (c) 2014 Tugdual de Kerviler
