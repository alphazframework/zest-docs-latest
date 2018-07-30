The Zest framework provides support for email sending using SMTP and php mailer

# SMTP Setup
To send mail using SMTP first update your Config.php file as follows:

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
To send an email simply do the following:

```php
<?php

namespace App\Controllers;
use Softhub99\Zest_Framework\View\View;
use Softhub99\Zest_Framework\Mail\Mail;

class Home extends \Softhub99\Zest_Framework\Controller\Controller
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
For sending email over smtp you just need add ```$mail->isSMTP(true);``` before ```$mail->send();```it become following

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
For sending html/template mail you just need change method name , instead of calling ```setContentPlain()```, You just need call ```setContentHTML()```

```php
//rest code .......
$mail->setSender('mail@example.com');
//Set the plain content of the mail.
$mail->setContentPlain('Example plain-content!');
//rest code .......

```
### Sending Mail with Attachment
To add an attachment to your mail simple add this line ``` $mail->addAttachment($file); ```

```php
//rest code .......
$mail->addAttachment("path/to/file");
//rest code .......

```
if you want send mutiple files just repeat this line what ever like you want attach.

### Setting replyTo Address
for setting reply to you just need call ```setReplyTo()``` method

```php
$mail->setReplyTo('example@example.com');
```
### Adding CC
To add cc addresses you need just call ```addCc();``` method

```php
$mail->addCc('CC@example.com');
```
### Adding BCC
To add bcc addresses you need just call ```addBcc();``` method

```php
$mail->addBcc('bcc@example.com');
```
