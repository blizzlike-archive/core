# realmlist

| Field                | Type         | Usage                                            |
| -------------------- | ------------ | ------------------------------------------------ |
| id                   | int(11)      | the unique account id                            |
| name                 | varchar(32)  | name of the realm                                |
| address              | varchar(32)  | IP address of the realm                          |
| localAddress         | varchar(255) | ?                                                |
| localSubnetMask      | varchar(255) | ?                                                |
| port                 | int(11)      | port where the realm is listen on                |
| icon                 | tinyint(3)   | the icon of the realm                            |
| realmflags           | tinyint(3)   | ?                                                |
| timezone             | tinyint(3)   | timezone of the realm                            |
| allowedSecurityLevel | tinyint(3)   | the minimum required gmlevel to access the realm |
| population           | float        | the current realm population                     |
| gamebuild_min        | int(11)      | ?                                                |
| gamebuild_max        | int(11)      | ?                                                |
| flag                 | tinyint(3)   | ?                                                |
| realmbuilds          | varchar(64)  | ?                                                |

## icon

| icon | type             |
| ---- | ---------------- |
| 0    | normal (PvE)     |
| 1    | PvP              |
| 4    | normal (RP PvE?) |
| 6    | RP               |
| 8    | RP PvP           |

## timezone

| value | timezone      |
| ----- | ------------- |
| 1     | development   |
| 2     | United States |
| 3     | Oceanic       |
| 4     | Latin America |
| 5     | Tournament    |
| 6     | Korea         |
| 7     | Tournament    |
| 8     | English       |
| 9     | German        |
| 10    | French        |
| 11    | Spanish       |
| 12    | Russian       |
| 13    | Tournament    |
| 14    | Taiwan        |
| 15    | Tournament    |
| 16    | China         |
| 17    | CN1           |
| 18    | CN2           |
| 19    | CN3           |
| 20    | CN4           |
| 21    | CN5           |
| 22    | CN6           |
| 23    | CN7           |
| 24    | CN8           |
| 25    | Tournament    |
| 26    | Test Server   |
| 27    | Tournament    |
| 28    | QA Server     |
| 29    | CN9           |

## population

the population is updated at regular intervals.
The formula to calculate the value in this field is:

    playerCount / maxPlayerCount * 2

| threshold | meaning |
| --------- | ------- |
| 0.5       | low     |
| 1.0       | medium  |
| 2.0       | high    |
