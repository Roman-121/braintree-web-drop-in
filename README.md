# Braintree Web Drop-in

A pre-made payments UI for accepting cards and alternative payments in the browser built using version 3 of the [Braintree JS client SDK](https://github.com/braintree/braintree-web).

If you have any feedback or questions, create an [issue](https://github.com/braintree/braintree-web-drop-in/issues) or [contact Braintree support](https://developers.braintreepayments.com/forms/contact).

## What's new

- Updated UI to easily accommodate multiple payment methods
- Not in an iframe; feel free to style Drop-in to blend in with your website
- Now available in [23 languages](https://braintree.github.io/braintree-web-drop-in/docs/current/#localization)
- Open source and open development

## Getting started

For setup and usage, see our [reference](https://braintree.github.io/braintree-web-drop-in/docs/current/).

## Full example

This is a full example of a Drop-in integration that only accepts credit cards.

 ```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Checkout</title>
  </head>
  <body>
    <div id="dropin-container"></div>
    <button id="submit-button">Purchase</button>

    <script src="https://js.braintreegateway.com/web/dropin/1.18.0/js/dropin.min.js"></script>

    <script>
      var submitButton = document.querySelector('#submit-button');

      braintree.dropin.create({
        authorization: 'CLIENT_AUTHORIZATION',
        selector: '#dropin-container'
      }, function (err, dropinInstance) {
        if (err) {
          // Handle any errors that might've occurred when creating Drop-in
          console.error(err);
          return;
        }
        submitButton.addEventListener('click', function () {
          dropinInstance.requestPaymentMethod(function (err, payload) {
            if (err) {
              // Handle errors in requesting payment method
            }

            // Send payload.nonce to your server
          });
        });
      });
    </script>
  </body>
</html>
```

## Browser support

Drop-in is supported in all browsers supported by the [Braintree JavaScript Client SDK](http://braintree.github.io/braintree-web/current/#browser-support).

## Customization

The design of Drop-in is intentionally opinionated, and while we aimed to make the design work in many scenarios, the design of your website may conflict with the default design of Drop-in. 

For minor UI customizations, [review our documentation](https://developers.braintreepayments.com/guides/drop-in/customization/javascript/v3#customize-your-ui).

For more substantial changes, you may [fork](https://help.github.com/articles/fork-a-repo/) Drop-in, make your desired changes and build the assets by running `npm run build`. By default, Drop-in uses a hosted version of the built stylesheet. To override this behavior and use a custom stylesheet instead, simply add `<link>` tag to your page with the id `braintree-dropin-stylesheet`. 

Drop-in uses the [Braintree JavaScript SDK](http://github.com/braintree/braintree-web). So if a fully customized UI is what you're looking for, Drop-in may be used as a reference implementation for using the JavaScript SDK.

## Releases

Subscribe to our [Google Group](https://groups.google.com/forum/#!forum/braintree-sdk-announce) to be notified when SDK releases go out.

## License

Drop-in is open source and available under the MIT license. See the [LICENSE](LICENSE) file for more info.
