# uptime

| Field         | Type         | Usage                                     |
| ------------- | ------------ | ----------------------------------------- |
| realmid       | int(11)      | the unique id of the realm                |
| starttime     | bigint(20)   | timestamp when the server was started     |
| startstring   | varchar(64)  | formated time when the server was started |
| uptime        | bigint(20)   | uptime of the realm in seconds            |
| onlineplayers | smallint(5)  | number of currently connected players?    |
| maxplayers    | smallint(5)  | the maximum number of players connected   |
| revision      | varchar(255) | ?                                         |
