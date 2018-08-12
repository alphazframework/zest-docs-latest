# Configuration

## General

- **App_Name =>** Name of Application.
- **App_Version =>** Version of app.
- **SHOW_ERRORS =>** Error. If on, shows error on display. If off, errors are on the log file. Recommended to be off.
- **Language =>** Site language.
- **Data_Dir =>** Default Data directory.
- **Session_Path =>** Default path for session storage.
- **THEME_PATH =>** Default theme/view path.
- **AUTO_CSRF_VERIFIED =>** If on auto verified csrf token.
- **CSRF_TIMESTAMP =>** csrf token should expire.
- **CRYPTO_KEY =>** Crypto key used for cryptography.
- **Maintenance =>** If enabled, site will show maintenance mode.
- **ROUTER_CACHE** => Set to true to enable caching, or false to disable caching. Default value is true.
- **ROUTE_CACHE_REGENERATE** Timestamp for cache file. After it expires, the cache file auto-refreshes. Default value is 3600 (1 hour).

## Database

- **DB_DRIVER =>** Drieve of database for now only supported MySQL.
- **DB_HOST =>** Database host/IP.
- **DB_NAME =>** Name of database that you want use.
- **DB_USER =>** Username of database.
- **DB_PASS =>** Password of databse.

## Email

- **SITE_EMAIL =>** Site Email address.
- **SMTP_HOST =>** SMTP host/IP.
- **SMTP_USER =>** Username of SMTP.
- **SMTP_PASS =>** Password of SMTP.
- **SMTP_PORT =>** Port of SMTP

## Auth

- **AUTH_DB_NAME =>** Name of database that you want use in auth.
- **AUTH_DB_TABLE =>** Name of database table that you want use in auth.
- **VERIFICATION_LINK =>** Default link for verification account/email.
- **RESET_PASSWORD_LINK =>** Default link for reset password.
- **IS_SMTP =>** If set to true send mail in auth over SMTP.
- **IS_VERIFY_EMAIL =>** If set to true verification of account/email is required.
- **STICKY_PASSWORD =>** Is password should be strong. 
- **AUTH_ERRORS =>** Default error msgs. 
- **SUCCESS =>** Default success msgs. 
- **AUTH_SUBJECTS =>** Default subjects of emails. 
- **AUTH_MAIL_BODIES =>** Defaults body of emails. 