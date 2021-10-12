# passport-daangn

[Passport](http://passportjs.org/) strategy for daangn authenticating

---

[![npm](https://img.shields.io/npm/v/passport-daangn.svg)](https://www.npmjs.com/package/passport-daangn)
[![build](https://img.shields.io/travis/rycando/passport-daangn.svg)](https://travis-ci.org/rycando/passport-daangn)
[![coverage](https://img.shields.io/coveralls/rycando/passport-daangn.svg)](https://coveralls.io/github/rycando/passport-daangn)

## Install

```bash
$ npm install passport-daangn
```

## Usage

#### Configure Strategy

The daangn authentication strategy authenticates users using a code.
The strategy requires a `verify` callback, which accepts these
credentials and calls `done` providing a user.

```js
passport.use(new LocalStrategy(function (access_token, done) {}));
```

##### Available Options

This strategy takes an optional options hash before the function, e.g. `new LocalStrategy({/* options */, callback})`.

The available options are:

- `codeField` - Optional, defaults to 'code'
- `env` - Optional, defaults to 'dev'
- `scope` - Optional, defaults to 'account/profile'
- `app_id` - Essential
- `app_secret` - Essential

Both fields define the name of the properties in the POST body that are sent to the server.

#### Parameters

By default, `LocalStrategy` expects to find credentials in parameters
named code. If your site prefers to name these fields
differently, options are available to change the defaults.

    passport.use(new LocalStrategy({
        codeField: 'authCode',
        env: 'live',
        scope: 'account/profile',
        app_id: '',
        app_secret: '',
      },
      function(access_token, done) {
        // ...
      }
    ));

The verify callback can be supplied with the `request` object by setting
the `passReqToCallback` option to true, and changing callback arguments
accordingly.

    passport.use(new LocalStrategy({
        codeField: 'authCode',
        env: 'live',
        scope: 'account/profile'
        passReqToCallback: true,
        app_id: '',
        app_secret: '',
      },
      function(req, access_token, done) {
        // request object is now first argument
        // ...
      }
    ));

#### Authenticate Requests

Use `passport.authenticate()`, specifying the `'daangn'` strategy, to
authenticate requests.

For example, as route middleware in an [Express](http://expressjs.com/)
application:

```js
app.post(
  "/login",
  passport.authenticate("daangn", { failureRedirect: "/login" }),
  function (req, res) {
    res.redirect("/");
  }
);
```

## License

[The MIT License](http://opensource.org/licenses/MIT)

Copyright (c) 2011-2015 Jared Hanson <[http://jaredhanson.net/](http://jaredhanson.net/)>
