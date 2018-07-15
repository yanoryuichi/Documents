# Pear-Mail_Mimeを使って添付メールを送信

```php
<?php

//error_reporting(0);

include 'Mail.php';
include 'Mail/mime.php' ;

$text = '日本語の文章';
$text = mb_convert_encoding($text, "ISO-2022-JP", "UTF-8");
$subject = 'テストメール';
$subject = mb_convert_encoding($subject, "ISO-2022-JP", "UTF-8");
$subject = mb_encode_mimeheader($subject, "ISO-2022-JP");
$html = '<html><body>HTML version of email</body></html>';
$file = 'test.txt';
$crlf = "\n";
$hdrs = array(
              'From'    => 'hanako@gmail.com',
              'Subject' => $subject,
              );

$mime = new Mail_mime(array('eol' => $crlf, 'text_charset' => 'ISO-2022-JP'));

$mime->setTXTBody($text);
#$mime->setHTMLBody($html);
$mime->addAttachment($file, 'text/plain');

$body = $mime->get();
$hdrs = $mime->headers($hdrs);

$mail =& Mail::factory('mail');
$mail->send('taro@gmail.com', $hdrs, $body);

?>
```

## 参考

- Pear::Mail_Mime http://pear.php.net/package/Mail_Mime/docs
- Pear::Mail http://pear.php.net/package/Mail/docs
