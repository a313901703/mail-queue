# mail-queue
基于Yii2 + redis的邮件队列

```
...
'components' => [
    ...
    'mailer'=>[
        'class' => 'common\components\mail\MailerQueue',
        'viewPath' => '@common/mail',
        'db'=>1,
        'key'=>'mails',
        'useFileTransport' => false,
        'transport' => [
            'class' => 'Swift_SmtpTransport',
            'host' => 'smtp.163.com',
            'username' => 'USERNAME',
            'password' => 'PASSWD',
            'port' => '25',
            'encryption' => 'tls',
        ],
        'messageConfig'=>[
            'charset'=>'UTF-8',
            'from'=>['USERNAME'=>'ADMIN'],
        ],
    ],
    ...
  ]
...

加入队列
Yii::$app->mailer->compose()->setTo()->setHtmlBody()->queue();

发送
Yii::$app->mailer->process();
```
