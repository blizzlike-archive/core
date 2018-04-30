# account

| Field                    | Type         | Usage                                          |
| ------------------------ | ------------ | ---------------------------------------------- |
| id                       | int(11)      | the unique account id                          |
| username                 | varchar(32)  | the login name of the account                  |
| sha_pass_hash            | varchar(40)  | the sha1 hash of USERNAME:PASSWORD             |
| gmlevel                  | tinyint(3)   | security level of the account                  |
| sessionkey               | longtext     |                                                |
| v                        | longtext     |                                                |
| s                        | longtext     |                                                |
| reg_mail                 | varchar(255) | ?                                              |
| token_key                | varchar(100) | ?                                              |
| email                    | text         | the email address of the account               |
| joindate                 | timestamp    | the date when the account was created          |
| last_ip                  | varchar(30)  | the IP used at the last login                  |
| last_attempt_ip          | varchar(30)  | the IP used at the last failed login?          |
| last_local_ip            | varchar(30)  | ?                                              |
| failed_logins            | int(11)      | the number of failed login attempts            |
| locked                   | tinyint(3)   | state if account has been locked or not        |
| lock_country             | varchar(2)   | ?                                              |
| last_login               | timestamp    | timestamp of the last login                    |
| last_pwd_reset           | timestamp    | timestamp of the last password reset           |
| online                   | tinyint(4)   | shows if the user is logged in and online      |
| expansion                | tinyint(3)   | the accounts available expansion               |
| mutetime                 | bigint(40)   | the timestamp when the account will be unmuted |
| mutereason               | varchar(255) | the reason why an account is muted             |
| muteby                   | varchar(50)  | the username of gm that muted the account?     |
| locale                   | tinyint(3)   | the gameclient locale                          |
| os                       | varchar(4)   | ?                                              |
| recruiter                | int(11)      | ?                                              |
| current_realm            | tinyint(3)   | id of the accounts current realm?              |
| banned                   | tinyint(1)   | shows if the user is banned or not             |
| mail_verif               | tinyint(1)   | ?                                              |
| remember_token           | varchar(100) | ?                                              |
| flags                    | int(10)      | ?                                              |
| security                 | varchar(255) | ?                                              |
| pass_verif               | varchar(255) | ?                                              |
| email_verif              | tinyint(1)   | shows if the user verified his email address   |
| email_check              | varchar(255) | ?                                              |
| nostalrius_token         | varchar(255) | ?                                              |
| nostalrius_token_enabled | tinyint(1)   | ?                                              |
| nostalrius_email         | text         | ?                                              |
| nostalrius_reason        | text         | ?                                              |

## username

> be aware of the client-side limitation of max 16 characters in username input field.

## sha_pass_hash

> be aware of the client-side limitation of max 16 characters in password input field.

    SELECT SHA1(CONCAT(UPPER(`username`), ':', UPPER('<pass>')));

## gmlevel

-- define existing levels
-- the required level for a command is defined in world db's command table

## locked

| value | description           |
| ----- | --------------------- |
| 0     | account is not locked |
| 1     | account is locked     |

## online

boolean
* 0 for offline?
* 1 for online?

## expansion

| value | description                |
| ----- | -------------------------- |
| 0     | WoW Classic                |
| 1     | WoW The Burning Crusade    |
| 2     | WoW Wrath of the Lich King |

The world server will block access to accounts with 0 in this field in the TBC and WotLK areas in-game.
The world server will block access to accounts with 1 in this field in the WotLK areas in-games.

## banned

boolean
* 0 for not banned?
* 1 for banned?

## email_verif

boolean value that defines if email address is verified or not.
This field is ignored until `ReqEmailVerification` is enabled in `realmd.conf`

| value | description                  |
| ----- | ---------------------------- |
| 0     | not verified / prevent login |
| 1     | verified / allow login       |
