# Github Action for Serverless

This Action wraps the [Serverless Framework](https://serverless.com) to enable common Serverless commands.

## Usage
An example workflow to deploy a project with serverless:


```
on:
  push:
    branches:
      - master
name: Deploy master branch
jobs:
  deploy:
    name: deploy
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: npm install
      uses: actions/npm@master
      with:
        args: install
    - name: serverless deploy
      uses: ollisala/github-action@master
      with:
        args: deploy
      env:
        SERVERLESS_ACCESS_KEY: ${{ secrets.SERVERLESS_ACCESS_KEY }}
        # or if using AWS creds directly
        # AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
        # AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        # If your serverless.yaml is not at the root directory, please add
        # PROJECT_DIR: <directory goes here>
```

## License

The Dockerfile and associated scripts and documentation in this project are released under the Apache-2 license.
