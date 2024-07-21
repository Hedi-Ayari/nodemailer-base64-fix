# nodemailer-base64-fix

A Node.js plugin for Nodemailer that fixes the issue of base64 images not displaying by converting them to CID-based inline attachments.

## Installation

```sh
npm install nodemailer-base64-fix
```
## Usage
```js
const nodemailer = require('nodemailer');
const base64Fix = require('nodemailer-base64-fix');

let transporter = nodemailer.createTransport({
  // your transport options
  plugin: base64Fix({
    cidPrefix: 'image_'
  })
});

let mailOptions = {
  from: 'sender@example.com',
  to: 'recipient@example.com',
  subject: 'Subject',
  html: '<img src="data:image/png;base64,..."> Some content here'
};

transporter.sendMail(mailOptions, (error, info) => {
  if (error) {
    return console.log(error);
  }
  console.log('Message sent: %s', info.messageId);
});
```