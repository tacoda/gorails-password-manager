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
- Add edit action
- Add edit view
- Add update action
- Add delete link to form
- Add destroy action
- Add dependent destroy to model associations for link table
- Add password partial

## Copy to Clipboard

- Grab icon image from heroicons
- Add to show view
- Rename hello_controller stimulus controller to clipboard_controller
- Implement navigator.clipboard functionality and update UI

## Sharing Passwords

- Add routes for shares

```sh
r routes -g shares
```

- Add link to share in password show view
- Create shares controller
- Add shares new view
- Add create action
- Add destroy action

## Roles and Permissions

- Add migration

```sh
r g migration AddRoleToUserPasswords role
r db:migrate
r c
```

```ruby
UserPassword.update_all(role: "owner")
```

- Add validation to UserPassword model
- Update Password controller to use role
- Update Shares controller to user role
- Update shares new view to include the role
- Add role to permitted parameters
- Add role on the password show view
- Add methods to UserPassword model
- Add before action to Password controller
- Add methods to Password model
- Push method logic into UserPassword and refactor Password call
- Update links in password show view to look at permissions
- Add before action to Shares controller
- Add conditions in views to hide links

## Styling

- Add nav
- Break out alerts to partial
- Break out nav to partial
- Adjust styling

## Deploy to Fly

```sh
r db:encryption:init
r credentials:edit --environment=production

# If no secret key base is defined
r secret
r credentials:edit --environment=production

fly launch
fly deploy

fly ssh console
bin/rails db:migrate
```
