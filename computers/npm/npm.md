## NPM Stuff

### Fix permissions if you can't install `-g` withouth `sudo`

- Verify installed at usr/local
`npm config get prefix`

- Change owner to current user
` sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}
`
