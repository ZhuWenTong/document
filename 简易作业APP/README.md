# 简易作业 
1. `BASE_API: http://113.98.60.90:8086  //飞力达亚太公网`
2. `BASE_API: http://192.168.17.31:8086 //飞力达亚太内网`

## 注意	
> 请求方式 post 

> 所有除登录外的请求都要带上SESSION

> SESSION失效重新登录时 将this作为参数传给全局登录函数重新获取SESSION

## 业务异常处理
1. data.code === 'S0002' 
	* session失效 需重新登录
2. data.code !== 'S0002' && !data.success
	* msg异常信息提示出来

## ajax接口
> `query{}` 之后单元格的值为对象query的属性

> `data[{}]` 之后单元格的值为数组data中每一项对象的属性 

| 请求场景 		| 地址	           					| 参数	   				| 返回值	           									|
|-----------|-----------------------------------|-----------------------|---------------------------------------------------|
| 登录    	 	| /login         					| username / password	| wms / sessionId / `resources[{}]`					|
|          	|                					| systemId 				| id / code / name / colorHex						|
|			|									|						|													|
| 搜索条件 		| /find/resource 					| id / wmsCode			| url / `propertyShares[{}]`    					|
|			|									|						| propId / propName / inputType / propCode			|
|			|									|						| value / regexp / redisName / redisData			|
|			|									|						|													|
| 搜索结果	   	| /takein/find/wmsBillList 			| `query{}`				| `data[{}]`										|
|			|									| dateStart	/ dateEnd	| wms_uuid / wms_no	/status_desc					|
|			|									| pageNo / pageSize		| busi_date / create_time / create_name				|
|			|									| wmsNo	/ wmsCode		| consignor	/ consignee	/ qty / wms_stock_qty		|
|			|									|						| tras_no / car_no_abr / sh_mode					|
|			|									|						| pallet_num / parcel_num / gross_weight			|
|			|									|						|													|
| 扫描收货条码	| /find/storage						| store_uuid / wms_code | store_uuid / store_code / store_type / wms_code	|
|			|									| store_type			| 													|
|			|									|						|													|
| 请求详情		| /takein/find/wmsBillList/details	| wms_uuid				| `billLists[{}]` / `qty{}`							|
|			|									|						| `b: ` wms_no / wms_list_id / wms_list_no / qty	|
|			|									|						| / wms_stock_qty / unit / wms_list_info_string		|
|			|									|						| `q: ` 											|
|			|									|						|													|
| 请求3个qty	| /takein/find/qty					| wms_uuid				| lpn_outter_qty / lpn_qty / idn_qty				|
|			|									|						|													|