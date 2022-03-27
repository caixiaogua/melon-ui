### melonUI简介

使用go语言打包的，基于chrome的桌面应用框架，类似electron，使用html5开发桌面应用，框架已经编译好了，直接可用于生产环境。

melonUI全新升级版，已完成与jsgo的整合，正式更名为melonbox，该项目已迁移至：
https://github.com/caixiaogua/melonbox

### 使用说明：
下载，解压，把做好html项目放入dist文件夹。


#### v4.0更新说明：
1. 可与jsgo进行整合，拥有无比强大的开发体验。了解jsgo：https://github.com/caixiaogua/jsgo
2. 目录中存在jsgo.exe文件，将会自动启动jsgo，否则，以普通模式启动。
3. 普通模式，只支持静态页面，静态目录为dist，首页为index.html，将web项目直接拷贝到该目录即可。
4. jsgo模式，内置丰富的接口函数，可混合编写js和go代码，并可编译为so文件。

```
//jsgo模式app.js范例
function main(){
	let path=ctx.Request.URL.Path;
	if(path=="/"){
		ctx.Header("Cache-Control", "no-cache");
		// ctx.File("dist/index.html");
		ctx.Header("Content-Type", "text/html");
		// return "<script>location.href='http://www.baidu.com/';</script>";
		return "jsgo.ok";
	}else if(path=="/item"){
		return api.import("item.js")();
	}else if(path=="/files"){
		return api.getList(".").map(x=>x.Name());
	}
	return "none";
}
```
