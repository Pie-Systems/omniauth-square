# OmniAuth Square

This gem contains the Square strategy for OmniAuth.

Square uses the OAuth2 flow, you can read about it here: https://developer.squareup.com/docs/auth.

## Scopes

This gem requires at least the following two scopes: `MERCHANT_PROFILE_READ` and `EMPLOYEES_READ`. See a full list of scopes [here](https://developer.squareup.com/docs/oauth-api/square-permissions).

## How To Use It

Add the strategy to your `Gemfile`:

    gem 'omniauth-square', git: 'https://github.com/ajsharp/omniauth-square.git'

Add the following to your `config/initializers/omniauth.rb`:
```ruby
Rails.application.config.middleware.use OmniAuth::Builder do
  provider :square, "consumer_key", "consumer_secret",
    {
      client_options: {
        connect_site: Rails.env.production? ? 'https://connect.squareup.com' : 'https://connect.squareupsandbox.com',
        site: Rails.env.production? ? 'https://connect.squareup.com' : 'https://connect.squareupsandbox.com'
      },
      scope: 'MERCHANT_PROFILE_READ EMPLOYEES_READ',
      raise_errors: true
    }
end
```

**Note:** Square uses a separate url for it's sandbox environment. The example above uses a sandbox URL in a non-production environment.

## License

Copyright (c) 2013 by [Daniel Archer](https://github.com/dja/), [Jen Aprahamian](https://github.com/jennifermarie/), [Adam Bouck](https://github.com/abouck/), [Ray Zane](https://github.com/rzane)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
