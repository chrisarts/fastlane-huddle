# INIT FASTLANE
on ios folder

```
fastlane init
```

* Select beta release config
* Fill your apple developer data

# Add Yarn plugin

```
fastlane add_plugin yarn
```

# Create lanes for yarn releases and patch config
Note: change `:beta` lane to `:private_lane`

```
patch_release
minor_release
major_release
```

# Add auto-changelog config

`yarn add -D auto-changelog`

Create the `.autochangelog` file with config:

```
{
  "output": "HISTORY.md",
  "template": "keepachangelog",
  "unreleased": true,
  "commitLimit": false
}
```

# Add ruby hooks to ensure git branch and generate data

* add the `before_all` ruby hook

# Add conventional commits

* Add lib to global npm: 
```
npm install -g commitizen
```

* Initialize commitizen using yarn: 
```
commitizen init cz-conventional-changelog --yarn --dev --exact
```

# Add husky
* Install husky
```
yarn add -D husky
```
* Add pre-commit hook
```
npx husky add .husky/pre-commit "yarn lint" 
```

* Add commit-msg hook
```
npx husky add .husky/commit-msg "echo 'Commit msg'"
```

* Add prepare-commit-msg
```
npx husky add .husky/prepare-commit-msg "exec < /dev/tty && git cz --hook || true"
```