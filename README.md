/* 离线地图API V2.1
 * 发布地址: http://www.xiaoguo123.com/p/baidumap_offline_v21
 * 百度地图图片即瓦片文件请自行下载，或联系(QQ群 616816128 验证：百度地图API)
 * 研究学习之用，禁止用于商业用途！
 * 原始文件获取地址：http://api.map.baidu.com/getscript?v=2.0
 * 地图API在线示例: http://developer.baidu.com/map/jsdemo.htm
 * 最后修改日期: 2017-12-04
 */

------技术交流QQ群 616816128 验证：百度地图API---------

说明：
1）离线地图不是万能的, 有些依赖在线的功能是无法使用的, 请自行扩展
2）请查看 离线地图示例demo.html 里面的示例，或者查看地图API在线示例: http://developer.baidu.com/map/jsdemo.htm
3) 地图API请查看百度官方说明: http://developer.baidu.com/map/reference/index.php
4）如有更新，请查看网站: http://www.xiaoguo123.com/p/baidumap_offline_v21
5）此API用户大家交流学习，本人没有能力提供太多的技术帮助
6）由于某些用途导致的商业纠纷，和本人无关

新增：
1）支持显示卫星混合地图，瓦片图放到 tiles_hybrid 目录下
2）支持支定义混合图，瓦片图放到 tiles_self 目录下
3）增加根据城市名称设置地图中心, 请自行扩展map_city.js
4）增加鼠标测距示例
5）增加鼠标绘制线面示例

增加新的瓦片图：
1）使用地图下载工具（如太乐地图下载）下载你要的地区和级别
2）务必导出瓦片图（百度格式），可以选择导出jpg或png图形
3）按需要修改map_load.js，指定瓦片图的路径，或者按默认的来
4）目录说请看图片： 目录说明.jpg

基本的使用方法如下：
1）加载离线地图必须的文件：
  <script type="text/javascript" src="offlinemap/map_load.js"></script>
  <link rel="stylesheet" type="text/css" href="offlinemap/css/map.css"/>

2）增加一个容器用来显示地图
<div id="map_demo"></div>

3）写JS脚本
<script type="text/javascript">  
	var map = new BMap.Map("map_demo");    // 创建Map实例
	map.centerAndZoom(new BMap.Point(116.404, 39.915), 7);  // 初始化地图,设置中心点坐标和地图级别
	map.setCurrentCity("武汉");          // 设置地图中心显示的城市 new！
	map.enableScrollWheelZoom(true);     //开启鼠标滚轮缩放
	map.addControl(new BMap.NavigationControl());   //缩放按钮
	map.addControl(new BMap.MapTypeControl( {mapTypes: [BMAP_NORMAL_MAP,BMAP_HYBRID_MAP]} ));   //添加地图类型控件 离线只支持普通、卫星地图; 三维不支持
</script>
