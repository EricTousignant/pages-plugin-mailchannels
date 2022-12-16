## Pages Plugins

# MailChannels Pages Plugin

This is a refactored version of the @cloudflare/pages-plugin-mailchannels plugin, which was based on the @cloudflare/pages-plugin-static-forms package.

[Original package documentation from Cloudflare.](https://developers.cloudflare.com/pages/platform/functions/plugins/mailchannels/)

Also fixed the bug that only returns 200 OK status codes.

## Installation

```sh
npm i --save https://github.com/yhorian/pages-plugin-mailchannels
```

## Usage

Copy the **_middleware.ts** file from this repository over to your own /functions folder. 

### Change the email inside to your own:
```js
const myEmail = "example@example.com"
```

Once compiled by Cloudflare Pages, the Function will capture anything from a form with a 'data-static-form-name' attribute set, such as:
```html
<body>
  <h1>Contact us</h1>
  <form data-static-form-name="contact">
    <label>Name <input type="text" name="name" /></label>
    <label>Email address <input type="email" name="email" /></label>
    <label>Message <textarea name="message"></textarea></label>
    <button type="Submit">
  </form>
</body>
```

On form submit, you'll get an email from 'Contact form' with all the relevant data from the [Mailchannel API](https://mailchannels.zendesk.com/hc/en-us/articles/4565898358413-Sending-Email-from-Cloudflare-Workers-using-MailChannels-Send-API). Some restrictions apply.

To use multiple middleware handlers, see this documentation on [Chaining middleware](https://developers.cloudflare.com/pages/platform/functions/middleware/).
