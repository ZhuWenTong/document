# 简易作业 
1. `BASE_API: http://113.98.60.90:8086  //飞力达亚太公网`
2. `BASE_API: http://192.168.17.31:8086 //飞力达亚太内网`
	
> 请求方式 post 

> 所有除登录外的请求都要带上SESSION

## 业务异常处理
1. data.code === 'S0002' 
	* session失效 需重新登录
2. data.code !== 'S0002' && !data.success
	* msg异常信息提示出来

## ajax接口
> `query{}` 表示 之后表格的值为对象query的属性

| 请求场景 		| url            			| params   				| data           									|
|-----------|---------------------------|-----------------------|---------------------------------------------------|
| 登录    	 	| /login         			| username / password	| resources / wms / sessionId						|
|          	|                			| systemId 				|       											|
|			|							|						|													|
| 搜索条件 		| /find/resource 			| id / wmsCode			| url / `propertyShares[{}]`    					|
|			|							|						| propId / propName / inputType / propCode			|
|			|							|						| value / regexp / redisName / redisData			|
|			|							|						|													|
| 搜索结果	   	| /takein/find/wmsBillList 	| `query{}`				| `data[{}]`										|
|			|							| dateStart	/ dateEnd	| wms_uuid / wms_no	/status_desc					|
|			|							| pageNo / pageSize		| busi_date / create_time / create_name				|
|			|							| wmsNo	/ wmsCode		| consignor	/ consignee	/ qty / wms_stock_qty		|
|			|							|						| tras_no / car_no_abr / sh_mode					|
|			|							|						| pallet_num / parcel_num / gross_weight			|
|			|							|						|													|
| 扫描收货条码	| /find/storage				| store_uuid / wms_code | `data{}`											|
|			|							| store_type			| store_uuid / store_code / store_type / wms_code	|