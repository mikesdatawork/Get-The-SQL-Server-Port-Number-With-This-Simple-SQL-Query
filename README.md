![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Get The SQL Server Port Number With This Simple SQL Query
**Post Date: September 16, 2015**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>Get the SQL Server Port Number with this Simple Query</p>      


## SQL-Logic
```SQL

use master;
set nocount on
 
declare @key    varchar(255)
declare @port   varchar(50)
 
-- get the port number using the serverproperty function and xp_regread
if charindex('\',convert(char(255), serverproperty('servername')),0) <>0
    begin
        set @key = 'software\microsoft\microsoft sql server\' + @@servicename + '\mssqlserver\supersocketnetlib\tcp'
    end
else
    begin
        set @key = 'software\microsoft\mssqlserver\mssqlserver\supersocketnetlib\tcp'
    end
exec master..xp_regread
    @rootkey    = 'hkey_local_machine'
,   @key        = @key
,   @value_name = 'tcpport'
,   @value      = @port output
 
select
    'ServerName'    = @@servername
,   'Port'      = convert(varchar(10), @port)
```


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

      
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

