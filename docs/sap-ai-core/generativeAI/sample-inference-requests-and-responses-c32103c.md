<!-- loioc32103c6218141d18e2432db6cec1e08 -->

# Sample Inference Requests and Responses

The following examples demonstrate common forecasting scenarios and show how different request parameters affect the response returned by the inference service.



## Successful Prediction \(200\): Request with Integer Timestamps

This example uses integer timestamps.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":2,"data":[{"timestamp":[1,2,3,4,5,6,7,8,9,10],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]}]}'
      
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[10.996417999267578,11.85465145111084]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[10.568910598754883,11.262651443481445],[11.472352027893066,12.359424591064453]]]],"result_timestamp":[[11,12]],"detected_interval":[{"unit":"integer","value":1}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>          
> ```



## Successful Prediction \(200\): Request with Date Timestamps

This example uses date-based timestamps.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":3,"data":[{"timestamp":["2020-01-01","2020-01-02","2020-01-03","2020-01-04","2020-01-05","2020-01-06","2020-01-07","2020-01-08","2020-01-09","2020-01-10"],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]}]}'
      
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[10.996417999267578,11.85465145111084,12.698359489440918]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[10.568910598754883,11.262651443481445,12.033546447753906],[11.472352027893066,12.359424591064453,13.541707992553711]]]],"result_timestamp":[["2020-01-11","2020-01-12","2020-01-13"]],"detected_interval":[{"unit":"day","value":1}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>          
> ```



## Successful Prediction \(200\): Request with SECONDDATE Timestamps

This example uses SECONDDATE timestamps.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":2,"data":[{"timestamp":["2020-01-01 00:00:01.001","2020-01-01 00:00:01.002","2020-01-01 00:00:01.003","2020-01-01 00:00:01.004","2020-01-01 00:00:01.005","2020-01-01 00:00:01.006","2020-01-01 00:00:01.007","2020-01-01 00:00:01.008","2020-01-01 00:00:01.009","2020-01-01 00:00:01.010"],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]}]}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[10.996417999267578,11.85465145111084]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[10.568910598754883,11.262651443481445],[11.472352027893066,12.359424591064453]]]],"result_timestamp":[["2020-01-01 00:00:01.011","2020-01-01 00:00:01.012"]],"detected_interval":[{"unit":"1e-7second","value":10000}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with LONGDATE Timestamps

This example uses LONGDATE timestamps.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":2,"data":[{"timestamp":["2020-01-01 00:00:01.001","2020-01-01 00:00:01.002","2020-01-01 00:00:01.003","2020-01-01 00:00:01.004","2020-01-01 00:00:01.005","2020-01-01 00:00:01.006","2020-01-01 00:00:01.007","2020-01-01 00:00:01.008","2020-01-01 00:00:01.009","2020-01-01 00:00:01.010"],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]}]}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[10.996417999267578,11.85465145111084]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[10.568910598754883,11.262651443481445],[11.472352027893066,12.359424591064453]]]],"result_timestamp":[["2020-01-01 00:00:01.011","2020-01-01 00:00:01.012"]],"detected_interval":[{"unit":"1e-7second","value":10000}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with output\_quantile

Returns all 21 quantiles in `quantile_result`.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":2,"data":[{"timestamp":[1,2,3,4,5,6,7,8,9,10],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]}],"options":{"output_quantile":true}}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[10.996417999267578,11.85465145111084]]],"quantile_result":[[[[7.5556230545043945,7.744816780090332],[10.193599700927734,10.68617057800293],[10.568910598754883,11.262651443481445],[10.570749282836914,11.3654203414917],[10.743620872497559,11.486021041870117],[10.795597076416016,11.586033821105957],[10.871317863464355,11.722585678100586],[10.889595031738281,11.743776321411133],[10.926765441894531,11.785883903503418],[10.986242294311523,11.841873168945312],[10.996417999267578,11.85465145111084],[11.025259017944336,11.946949005126953],[11.073755264282227,11.965944290161133],[11.138389587402344,12.05129623413086],[11.204987525939941,12.129083633422852],[11.208433151245117,12.215331077575684],[11.261232376098633,12.271505355834961],[11.352106094360352,12.344038009643555],[11.472352027893066,12.359424591064453],[11.682449340820312,12.531235694885254],[12.57781982421875,13.738334655761719]]]],"selected_quantile_result":null,"confidence_interval_output":[[[[10.568910598754883,11.262651443481445],[11.472352027893066,12.359424591064453]]]],"result_timestamp":[[11,12]],"detected_interval":[{"unit":"integer","value":1}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with a Custom confidence\_interval

Sets a 95% interval. The bounds in `confidence_interval_output` are the q=0.025 and q=0.975 quantiles \(index 0 is the lower bound, index 1 the upper\), which are wider than the default 80% interval.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":3,"data":[{"timestamp":[1,2,3,4,5,6,7,8,9,10],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]}],"options":{"confidence_interval":0.95}}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[10.996417999267578,11.85465145111084,12.698359489440918]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[8.544864654541016,8.847824096679688,9.358936309814453],[12.242055892944336,13.285673141479492,14.644306182861328]]]],"result_timestamp":[[11,12,13]],"detected_interval":[{"unit":"integer","value":1}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with point\_forecast: mean

This example uses `point_forecast` set to `mean`.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":5,"data":[{"timestamp":[1,2,3,4,5,6,7,8,9,10],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]}],"options":{"point_forecast":"mean"}}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[11.013999938964844,11.864879608154297,12.777382850646973,13.760469436645508,14.703609466552734]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[10.568910598754883,11.262651443481445,12.033546447753906,12.75979232788086,13.503268241882324],[11.472352027893066,12.359424591064453,13.541707992553711,14.721451759338379,15.873589515686035]]]],"result_timestamp":[[11,12,13,14,15]],"detected_interval":[{"unit":"integer","value":1}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with point\_forecast: mean and Custom quantile\_levels

Uses trapezoidal integration over 9 quantile levels to compute the distribution mean, recommended for intermittent-demand forecasting. When `quantile_levels` is set, the same levels are returned in `selected_quantile_result`.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":10,"data":[{"timestamp":["2007-12-10","2007-12-12","2007-12-14","2007-12-16","2007-12-18","2008-01-15","2008-01-17","2008-01-19","2008-01-21","2008-01-23","2008-01-25","2008-01-27","2008-01-29","2008-02-02","2008-02-04","2008-02-06","2008-02-08","2008-02-10","2008-02-12","2008-02-14"],"target":[[10.25,11.99,13.27,13.13,11.02,10.43,12.23,13.88,15.33,16.72,15.64,14.4,14.17,13.98,16.14,18.78,19.44,19.52,17.68,16.84]],"past_covariates":{"airtemperature":[15.44,17.28,17.95,15.87,13.54,12.11,12.31,15.11,17.17,17.84,16.12,14.25,12.07,12.34,15.25,16.98,17.99,15.71,13.3,12.13]},"future_covariates":{"airtemperature":[12.88,15.05,17.31,17.83,15.86,13.48,11.94,12.97,15.1,16.82]}}],"options":{"point_forecast":"mean","quantile_levels":[0.1,0.2,0.3,0.4,0.5,0.6,0.7,0.8,0.9]}}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[17.364219665527344,18.583675384521484,20.325830459594727,20.580018997192383,19.99493408203125,18.86580467224121,18.245637893676758,18.469654083251953,19.736997604370117,21.58102035522461]]],"quantile_result":null,"selected_quantile_result":[[[[15.861515998840332,16.566572189331055,17.601001739501953,17.5913143157959,16.712663650512695,15.692886352539062,14.958240509033203,14.887096405029297,15.703776359558105,16.815309524536133],[16.54750633239746,17.45974349975586,18.831235885620117,18.918731689453125,18.04950714111328,16.962177276611328,16.238269805908203,16.250152587890625,17.206666946411133,18.629743576049805],[16.925079345703125,17.97675323486328,19.4957275390625,19.65349578857422,18.867145538330078,17.7641658782959,17.089292526245117,17.15414047241211,18.24173355102539,19.864036560058594],[17.196815490722656,18.338701248168945,20.019752502441406,20.14012908935547,19.521574020385742,18.366859436035156,17.71973419189453,17.89889907836914,19.033889770507812,20.79290771484375],[17.415781021118164,18.653329849243164,20.379512786865234,20.599533081054688,20.037200927734375,18.89378547668457,18.311809539794922,18.51116943359375,19.729907989501953,21.644052505493164],[17.636810302734375,18.955204010009766,20.824752807617188,21.066661834716797,20.60116195678711,19.432884216308594,18.835208892822266,19.10914421081543,20.476547241210938,22.44400978088379],[17.886484146118164,19.31573486328125,21.328678131103516,21.669452667236328,21.163698196411133,20.040342330932617,19.47285270690918,19.830299377441406,21.19437026977539,23.298524856567383],[18.168689727783203,19.733245849609375,21.82098388671875,22.306446075439453,21.927082061767578,20.73362922668457,20.21141815185547,20.625232696533203,22.266944885253906,24.463993072509766],[18.715164184570312,20.369441986083984,22.770782470703125,23.372516632080078,23.141986846923828,21.949920654296875,21.426950454711914,21.991235733032227,23.776165008544922,26.299983978271484]]]],"confidence_interval_output":[[[[15.861515998840332,16.566572189331055,17.601001739501953,17.5913143157959,16.712663650512695,15.692886352539062,14.958240509033203,14.887096405029297,15.703776359558105,16.815309524536133],[18.715164184570312,20.369441986083984,22.770782470703125,23.372516632080078,23.141986846923828,21.949920654296875,21.426950454711914,21.991235733032227,23.776165008544922,26.299983978271484]]]],"result_timestamp":[["2008-02-16","2008-02-18","2008-02-20","2008-02-22","2008-02-24","2008-02-26","2008-02-28","2008-03-01","2008-03-03","2008-03-05"]],"detected_interval":[{"unit":"day","value":2}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with enhanced\_forecast

This example enables `enhanced_forecast` to generate improved forecast predictions.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":2,"data":[{"timestamp":[1,2,3,4,5,6,7,8,9,10],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]}],"options":{"enhanced_forecast":true}}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[10.990999221801758,11.929146766662598]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[10.529675483703613,11.302016258239746],[11.476777076721191,12.441227912902832]]]],"result_timestamp":[[11,12]],"detected_interval":[{"unit":"integer","value":1}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with cross\_learning

Use when series are from related domains and cross-series information would be signal rather than noise.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":2,"data":[{"timestamp":[1,2,3,4,5,6,7,8,9,10],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]},{"timestamp":[1,2,3,4,5,6,7,8,9,10],"target":[[10.0,9.0,8.0,7.0,6.0,5.0,4.0,3.0,2.0,1.0]]}],"options":{"cross_learning":true}}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[10.75124454498291,11.541213989257812]],[[0.1672377586364746,0.0]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[10.398977279663086,11.130542755126953],[11.103979110717773,12.020644187927246]]],[[[0.0,0.0],[0.6594223976135254,0.0]]]],"result_timestamp":[[11,12],[11,12]],"detected_interval":[{"unit":"integer","value":1},{"unit":"integer","value":1}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with point\_forecast: hierarchical\_forecast

Six leaf series carry `country`, `city`, and `district` labels, but `hierarchical_levels` requests reconciliation only at `["country", "city"]`. The response is a tree containing exactly those two levels: country nodes with city children. The unlisted `district` key does not add further depth. No timestamps are provided, so `result_timestamp` and `detected_interval` are empty.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":4,"data":[{"target":[[10,11,12,13,14,15]]},{"target":[[8,9,10,11,12,13]]},{"target":[[6,7,8,9,10,11]]},{"target":[[5,6,7,8,9,10]]},{"target":[[4,5,6,7,8,9]]},{"target":[[3,4,5,6,7,8]]}],"options":{"point_forecast":"hierarchical_forecast","hierarchical_labels":[{"country":"germany","city":"berlin","district":"mitte"},{"country":"germany","city":"berlin","district":"charlottenburg"},{"country":"germany","city":"hamburg","district":"altona"},{"country":"germany","city":"hamburg","district":"harburg"},{"country":"france","city":"paris","district":"montmartre"},{"country":"france","city":"paris","district":"marais"}],"hierarchical_levels":["country","city"]}}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":null,"result_timestamp":[],"detected_interval":[],"all_null_targets":[],"hierarchical_result":[{"france":[[18.548839569091797,20.04424476623535,21.7530460357666,23.45072364807129]],"__children__":[{"paris":[[52.097679138183594,55.08848476409912,58.506086349487305,61.90144443511963]]}]},{"germany":[[29.548839569091797,31.044241905212402,32.753045082092285,34.45072364807129]],"__children__":[{"berlin":[[22.548839569091797,24.04424285888672,25.75304126739502,27.45072078704834]]},{"hamburg":[[18.548839569091797,20.04424476623535,21.7530460357666,23.45072364807129]]}]}],"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with Clipping

This example applies clipping to constrain forecast values between the specified `clip_min` and `clip_max` bounds.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":3,"data":[{"timestamp":[1,2,3,4,5,6,7,8,9,10],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]]}],"options":{"clip_min":0,"clip_max":11}}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[10.996417999267578,11.0,11.0]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[10.568910598754883,11.262651443481445,12.033546447753906],[11.472352027893066,12.359424591064453,13.541707992553711]]]],"result_timestamp":[[11,12,13]],"detected_interval":[{"unit":"integer","value":1}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Successful Prediction \(200\): Request with Deterministic Rules

Overwrites the forecast at every future step where the `is_holiday` covariate equals `1`.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"horizon":3,"data":[{"timestamp":[1,2,3,4,5,6,7,8,9,10],"target":[[1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0]],"past_covariates":{"is_holiday":[0,0,0,0,0,0,0,0,0,0]},"future_covariates":{"is_holiday":[0,1,0]}}],"options":{"rules":[{"covariate":"is_holiday","operator":"==","threshold":1,"forecast_value":0.0}]}}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"result":[[[11.048547744750977,0.0,12.874539375305176]]],"quantile_result":null,"selected_quantile_result":null,"confidence_interval_output":[[[[10.74734878540039,11.256742477416992,12.25273609161377],[11.459436416625977,12.39759635925293,13.73572063446045]]]],"result_timestamp":[[11,12,13]],"detected_interval":[{"unit":"integer","value":1}],"all_null_targets":[],"hierarchical_result":null,"group_results":null}
>     
> ```



## Unprocessable Content \(422\): Missing Required horizon

This example omits the required `horizon` field from the request body.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{"data":[{"timestamp":["2020-01-01","2020-01-02"],"target":[[1.0,2.0]]}]}'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {"detail":[{"type":"missing","loc":["body","horizon"],"msg":"Field required","input":{"data":[{"timestamp":["2020-01-01","2020-01-02"],"target":[[1.0,2.0]]}]}}]}
>     
> ```



## Bad Request \(400\): Invalid Timestamp Format

This example uses timestamps in the unsupported `MM/DD/YYYY` format. The `timestamp` field must use a supported format such as `YYYY-MM-DD`, `YYYY-MM-DD HH:MM:SS`, `YYYY-MM-DD HH:MM:SS[.fraction]`, `HH:MM:SS`, or an integer value.

**Request**

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{
    "horizon": 2,
    "data": [
      {
        "timestamp": ["01/01/2020", "01/02/2020", "01/03/2020"],
        "target": [[1.0, 2.0, 3.0]]
      }
    ]
  }'
    
```

**Response**

> ### Output Code:  
> ```
> 
> {
>   "detail": "timestamp must match one supported format: YYYY-MM-DD, YYYY-MM-DD HH:MM:SS, YYYY-MM-DD HH:MM:SS[.fraction], HH:MM:SS, or INTEGER"
> }
>     
> ```

> ### Note:  
> The request fails because the timestamps use the unsupported `MM/DD/YYYY` format. Use a supported timestamp format, for example, `2020-01-01`.

