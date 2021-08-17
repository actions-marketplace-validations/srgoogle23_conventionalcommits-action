# Actions - Conventional Commits 1.0.0

This repository contains a GitHub Actions which, if used, will check the semantics used in commit titles, titles and contents of pull requests, to check if they meet the design pattern.

## Installation

In `.github/workflows/` create a file called `main.yml`, with the following content:

```yml
name: Testes

on: [pull_request, push]

jobs:
  conventional-commits-checker:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Use Node.js
        uses: actions/setup-node@v1
        with:
          node-version: '12.x'
      - run: cd .github/conventionalcommits && npm install
      - run: cd .github/conventionalcommits && npm run build --if-present

      - name: conventional-commits-checker
        id: hello
        uses: ./.github/conventionalcommits/
```
Right after that, copy the contents of our latest release to the folder `.github/conventionalcommits/`.

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
