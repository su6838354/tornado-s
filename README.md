虽然淘宝nodejs中间层做前后端分离是个不错的思路，基于nodejs和前端开发使用同样的js渲染模板来完成。但是不适用于现有小团队：框架复杂、对开发人员js素质要求较高、部署项目较多、同时线上调试也存在一些不确定性因素。因此，针对小团队现状，试图构建一个简单的前后端分离的方案，适用于初创小团队，便于前后端各自专注于开发，同时部署方便且兼容SEO。
基本思路：tornado按目录进行渲染，url与目录成对应关系，前端在模板页起始处使用tornado模板语言获取该页所需数据用于页面渲染。同时框架也提供API接口，用于ajax交互使用。

针对tornado框架小改进：

1. override RequestHandler中的write方法，支持datetime对象的序列化。默认以时间戳方式输出。可通过override default_json_decoder方法来自定义。
2. 重新配置日志格式，日志改为按天midnight切割，同时也修改了多进程时的返回值，方便各进程独自写日志。
3. 暂时还没想到 _


运行命令行:
python server.py -port=80 -config=config/server.ini 
