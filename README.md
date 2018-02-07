## Clone the repo
```
$ git clone https://github.com/sidgs/pcf-app-deployment.git
```
## Add PCF environment variables
```
export PCF_API=xxxx
export PCF_ORG=xxx
export PCF_SPACE=xxx
export PCF_DOMAIN=xxx
export APIGEE_ORG=xxx
export APIGEE_ENV=xxx
```

## Login PCF
```
$ cf api https://api.system.apigee-cf.com --skip-ssl-validation
$ cf login 
```

## Validate  apigee service plan 'org'  
```
$ cf marketplace
$ cf service 
```

if plan 'org' is not persent add plan
```
$ cf create-service apigee-edge org org -c '{"env":"prod","org":"tech-brief"}'
```



## Create multiple (500) nodeJS apps
```
$ ansible-playbook helloapp_bind.yml --extra-vars "start_index=0 end_index=500 apigee_user=xxxx apigee_password=xxxxx"

```
Note: Run the above simultaneously to load apps in parallel 
ex: 
- start_index=0 end_index=500
- start_index=501 end_index=1000
- start_index=1001 end_index=1500
- start_index=1501 end_index=2000 
- ... 


### examples of apps created 
```
name                             requested state   instances   memory   disk   urls
app-0                            started           1/1         128M     1G     app-0.apps.apigee-cf.com
app-1                            started           1/1         128M     1G     app-1.apps.apigee-cf.com
app-2                            started           1/1         128M     1G     app-2.apps.apigee-cf.com
```

## Remove multiple (500) nodeJS apps
```
$ ansible-playbook helloapp_unbind.yml --extra-vars "apps_count=500 "
```