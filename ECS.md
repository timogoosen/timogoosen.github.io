## ECS

If you keep getting this error:

```

Error: InvalidParameterException: The new ARN and resource ID format must be enabled to propagate tags. Opt in to the new format and try again.


```

Then you can try:

```
aws ecs put-account-setting-default --name serviceLongArnFormat --value enabled
aws ecs put-account-setting-default --name taskLongArnFormat --value enabled
aws ecs put-account-setting-default --name containerInstanceLongArnFormat --value enabled
aws ecs put-account-setting-default --name awsvpcTrunking --value enabled  # optional 
aws ecs put-account-setting-default --name containerInsights --value enabled  # optional 

```



