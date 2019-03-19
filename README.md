# mailpecker
Wrapper around PHP IMAP to fetch and send PEC (Posta Elettronica Certificata) mails.

# Usage

## Reading mail
```php
$inbox = new mailpecker\imap([
  'host' => 'imap.example.com',
  'port' => 993,
  'user' => 'mailuser',
  'pass' => 'mailpass',
  'mailbox' => 'INBOX'
])
if($inbox !== FALSE){
  foreach($inbox->search($filters) as $mail){
    printf("Subject: %s\n", $mail->getSubject());
    printf("Message: %s\n\n", $mail->getBody());
  }
}
```

## Sending mail
```php
$outbox = new mailpecker\smtp([
  'host' => 'smtp.example.com',
  'port' => 465,
  'user' => 'mailuser',
  'pass' => 'mailpass'
]);
if($outbox !== FALSE){
  $outbox->setSubject('My PEC mail is coming!');
  $outbox->setBody('Here is the mail body');
  $outbox->send();
}
```
