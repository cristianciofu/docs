<a name="troubleshooting"></a>

## Troubleshooting

If you're having a problem installing Flarum, check out the [Installation tag](http://discuss.flarum.org/t/installation) on the support forum. Someone might've had the same problem as you! If not, start a discussion and we'll do our best to help.

<a name="configuring-smtp"></a>

## Configuring SMTP

There's currently no GUI to configure SMTP (see [#258](https://github.com/flarum/core/issues/258)). For now you can enter your details in manually in the `settings` database table using a tool like phpMyAdmin:

```
mail_driver: smtp
mail_host: ...
mail_from: ...
mail_port: ...
mail_username: ...
mail_password: ...
mail_encryption: ...
```
