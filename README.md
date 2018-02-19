# Testelm

To start your Phoenix app:

  * Install dependencies with `mix deps.get`
  * Install Node.js dependencies with `npm install`
  * Start Phoenix endpoint with `mix phoenix.server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.

Ready to run in production? Please [check our deployment guides](http://www.phoenixframework.org/docs/deployment).

## Learn more

  * Official website: http://www.phoenixframework.org/
  * Guides: http://phoenixframework.org/docs/overview
  * Docs: https://hexdocs.pm/phoenix
  * Mailing list: http://groups.google.com/group/phoenix-talk
  * Source: https://github.com/phoenixframework/phoenix
  
## Getting Start

### Phoenix

#### development

1. copy config/dev.exs.example to config/dev.exs
2. replace private_key and secret_key_base in config/dev.exs
3. install dependencies and run server

` mix deps.get && mix phoenix.server  `

4. Using a browser, go to http://localhost:4000/?xtoken=

#### production

1. copy config/prod.secret.exs.example to config/prod.secret.exs
2. replace private_key、secret_key_base、host and redis_host in config/prod.secret.exs
3. how to deploy

use [distillery](https://github.com/bitwalker/distillery)

### Rails

1. add jwt gem

` gem 'jwt' `

2. set a chat_token to include user info

```ruby
# app/helpers/application_helper.rb
CHATROOM_ADMIN_LIST = [1,....] #user id

def chat_token
    payload = {
      iss: #user name
      sub: #user unique name
      adi: #user is a admin or not
    }
    JWT.encode payload, private_key, 'HS256' # same as phoenix private_key
end
```
3. pass chat_token

```html
<iframe frameborder="0" name="Iframe1" src="https://localhost:4000/?xtoken=<%= chatroom_token %>" width="100%" height="450" scrolling="no"></iframe>
```






