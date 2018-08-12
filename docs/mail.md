The Zest framework provides support for sending email using SMTP and phpMailer.

# SMTP Setup
To send email using SMTP, first update your `Config.php` file as follows:

```php

/**
 * SMPT Host
 *
 * @var string
 */
const SMPT_HOST = "your-smtp-host";
/**
 * SMPT User
 *
 * @var string
 */
const SMPT_USER = "your-smtp-user";
/**
 * SMPT Pass
 *
 * @var string
 */
const SMPT_PASS = "your-smtp-pass";
/**
 * SMPT Port
 *
 * @var int
 */
const SMPT_PORT = 111;

```

# Sending Mail
To send an email, simply do the following:

```php
<?php

namespace App\Controllers;
use Zest\View\View;
use Zest\Mail\Mail;

class Home extends \Zest\Controller\Controller
{

    public function index()
    {
        $mail = new Mail;
        //Set subject.
        $mail->setSubject('Example mail');
        //Sender, like support@example.com
        $mail->setSender('mail@example.com');
        //Set the plain content of the mail.
        $mail->setContentPlain('Example plain-content!');
        //Add a receiver of the mail (you can add more than one receiver too).
        $mail->addReceiver('example@gmail.com');
        //Finally send the mail.
        if ($mail->send()) {
            echo "email send";
        } else {
            echo "email not send";
        }
    }
}

```

## Sending SMTP email
For sending email over SMTP, you just need to add ```$mail->isSMTP(true);``` before ```$mail->send();```. It becomes the following:

```php
//rest code .......
$mail->isSMTP(true);
//Finally send the mail.
if ($mail->send()) {
   echo "email send";
} else {
   echo "email not send";
}

```
### Sending Mail with Template/HTML
For sending HTML/template mail, you just need change the method name. Instead of calling ```setContentPlain()```, you just need call ```setContentHTML()```

```PHP
//rest code .......
$mail->setSender('mail@example.com');
//Set the plain content of the mail.
$mail->setContentPlain('Example plain-content!');
//rest code .......

```
### Sending email with an attachment.
To add an attachment to your mail simple add this line ``` $mail->addAttachment($file); ```

```PHP
//rest code .......
$mail->addAttachment("path/to/file");
//rest code .......

```
If you want to send mutiple files, just repeat this line with whatever you want to attach.

### Setting a "reply to" address.
For setting a "reply to" address, you just need to call the ```setReplyTo()``` method.

```php
$mail->setReplyTo('example@example.com');
```
### Adding CC
To add CC addresses, you just need to call the ```addCc();``` method.

```php
$mail->addCc('CC@example.com');
```
### Adding BCC
To add BCC addresses, you just need to call the ```addBcc();``` method.

```php
$mail->addBcc('bcc@example.com');
```
