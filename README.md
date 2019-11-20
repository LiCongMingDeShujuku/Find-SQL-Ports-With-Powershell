![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 使用Powershell查找SQL Ports
#### Find SQL Ports With Powershell
**发布-日期: 2016年11月7日 (评论)**

![#](images/find-sql-ports-with-powershell.png?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
假设你正在查看另一个数据库服务器，而且希望确保正确配置所有端口。你可能会冲动地登录到服务器，并从那里检查端口，你可能会发现比起在本地运行某些程序进行检查，登录到服务器就有些麻烦。 Powershell就可以实现。
如果你运行的是Server 2012或更高版本， 所有的Powershell cmdlet都已存在，你只需要知道要运行什么。 用这个简单的语句。 通过使用PSSESSION，你就可以远程连接到服务器，并获取所有“SQL”端口信息。
用Powershell逻辑（logic）来查找信息的方法如下：



## English
Ok; so you’re looking at another database server, and you want to make sure all the ports are properly configured. You might have the impulse to login to the server, and check the ports out from there, but at this stage you might find logging into the server is a bit annoying if you can just run something locally. Powershell to the rescue.
If you’re running Server 2012 or later; all the Powershell cmdlets are already there; you just need to know what to run. Take this little statement. Using PSSESSION you can connect remotely to the server, and get all the "SQL" port information.
The powershell logic to do that is here:


---
## Logic
```Powershell
enter-pssession "MyServerName"
 
Get-NetFirewallRule `
 
| Where { $_.Enabled -eq ‘True’ -and $_.Direction -eq ‘Inbound’ -and $_.'displayname' -like "*sql*" } `
 
| select displayname, enabled, action, direction `
 
| out-string -width 98
 
exit-pssession



```



[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

