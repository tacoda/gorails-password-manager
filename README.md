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

## Adding Models

```sh
r g model Password url username password
r g model UserPassword user:belongs_to password:belongs_to
```
