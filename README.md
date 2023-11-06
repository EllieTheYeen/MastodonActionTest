# Mastodon Action Test
This is just a test if GitHub actions can make Mastodon post for use in Jekyll blogs to add Mastodon comments to them and such.

This is to detect new posts and post them to Mastodon and save the id in a csv file since that is the most convenient format for this due to appendability.

Feel free to do what you want with this and an example is below that you can put in 
`.github/workflows/mastodonactiontest.yml`
of your repository and do not forget to set the `MASTODON_TOKEN` secret for the whole thing to work and set the settings such as the right Mastodon instance and Jekyll path correctly
```yaml
name: mastodonactiontest
on:
  push:
    branches:
      - main
  #workflow_dispatch:
jobs:
  mastodonactiontest:
    runs-on: ubuntu-latest
    name: mastodonactiontest
    environment: myenv
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: mastodonactiontest
        uses: EllieTheYeen/MastodonActionTest@v1
        env:
          MASTODON_TOKEN: ${{ secrets.MASTODON_TOKEN }}
        with:
          name: Mastodon Action Test
          email: 42704150+EllieTheYeen@users.noreply.github.com
          branch: main
          instance: https://botsin.space
          blogbase: https://ellietheyeen.github.io/Test
```