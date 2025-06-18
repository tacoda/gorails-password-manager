# Password Manager

# Notes

## Creating the app

```sh
r new gorails-password-manager -d postgresql --css tailwind
```

## Adding Devise

```sh
bundle add devise
r g devise:install
# Add suggested lines
r g devise:views
r g devise User
r db:migrate
```

## Adding Initial Models

```sh
r g model Password url username password
r g model UserPassword user:belongs_to password:belongs_to
```

- Add model relations

## Adding ActiveRecord Encryption

```sh
r db:encryption:init
r credentials:edit --environment=development
# Generates master key for environment
```

- Add model encrypt calls

```sh
r db:migrate
r c
```

```ruby
Password.create!(url: "twitter.com", username: "whatever", password: "password1234$")
Password.last.username
Password.last.password
Password.find_by_username("whatever")
Password.where(username: "whatever")
```

## Add UI

- Add password routes
- Add password controller

```sh
bin/dev
```

- Update application layout
- Add password index view
- Add new and create actions
- Add new view and form partial
- Add password model validations
- Add error rendering to form partial
- Add password show action
- Extract lookup to before action
- Add show view
