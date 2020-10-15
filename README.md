Spree-Html-Invoice
=======

This extension provides a "Print Invoice" button on the Admin Orders view screen which opens a printable html page with the order details.

Try Spree Html Invoice for Spree 3-1 with direct deployment on Heroku:

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/vinsol-spree-contrib/spree-demo-heroku/tree/spree-html-invoice-3-1)

Try Spree Html Invoice for Spree 3-4 with direct deployment on Heroku:

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/vinsol-spree-contrib/spree-demo-heroku/tree/spree-html-invoice-3-4)

Try Spree Html Invoice for Spree 4-1 with direct deployment on Heroku:

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/vinsol-spree-contrib/spree-demo-heroku/tree/spree-html-invoice-4-1)

Installation
------------

1. Add this extension to your Gemfile with this line:

  #### Spree > 3.3

  ```ruby
    gem 'spree_html_invoice', git: 'https://github.com/vinsol-spree-contrib/spree-html-invoice', branch: 'master'
  ```

  #### Spree <= 3.3

  ```ruby
    gem 'spree_html_invoice', git: 'https://github.com/vinsol-spree-contrib/spree-html-invoice', branch: 'X-X-stable'
  ```

  The `branch` option is important: it must match the version of Spree you're using.
  For example, use `3-0-stable` if you're using Spree `3-0-stable` or any `3.0.x` version.


2. Install the gem using Bundler:
  ```ruby
    bundle install
  ```

3. Configure your logo and footer text or more. It's easy as it's html.

Configuration
==============

1. Set the logo path preference to include your store / company logo.
    ```ruby
    Spree::HtmlInvoice::Config.set(html_invoice_logo_path: <"company-logo.png">)
    ```
    Somewhere in your asset path

2. Override any of the partial templates. they are address, footer, totals, header, thanks , and the line_items. The whole tanks is wrapped in a thanks hook, so replace or add at will.

3. Set `Spree::HtmlInvoice::Config.set(:suppress_anonymous_address)` option to get blank addresses for anonymous email addresses (as created by my spree_last_address extension for empty/unknown user info)

4. Enable packaging slips, by setting
  ```ruby
  Spree::HtmlInvoice::Config.set(print_buttons: "invoice,packaging_slip")  #comma separated list
  ```

  Use above feature for your own template if you want. For each button_name, define a subsection with header, print, and thanks, in your locale.

Contributions welcome

Testing
=======

  #### Spree >= 3.1

  For Building Dependencies:
  ```shell
  appraisal install
  ```

  The dummy app can be regenerated by using:
  ```shell
  appraisal spree-3-1 rake test_app

  ```
  This will run rake test_app using the dependencies configured for Spree 3.1. Similarly you can use spree-3-2 and spree-master for generating dummy applications using dependencies for Spree 3.2 and latest version of Spree


  ```shell
  appraisal spree-3-1 rspec
  ```
  This will run rspec using the dependencies configured for Spree 3.1. Similarly you can use spree-3-2 and spree-master to run rspec using dependencies for Spree 3.2 and latest version of Spree


  #### Spree 3.0 and Spree 2.x

  First bundle your dependencies, then run `rake`. `rake` will default to building the dummy app if it does not exist, then it will run specs. The dummy app can be regenerated by using `rake test_app`.

  ```shell
  bundle
  bundle exec rspec spec
  ```

Contributing
=========

1. Fork the repo.
2. Clone your repo.
3. Run `bundle install`.
4. Run `bundle exec rake test_app` to create the test application in `spec/test_app`.
5. Make your changes.
6. Ensure specs pass by running `bundle exec rspec spec`.
7. Submit your pull request.