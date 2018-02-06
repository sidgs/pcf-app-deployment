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
$ ansible-playbook helloapp_bind.yml --extra-vars "apps_count=500 apigee_user=xxxx apigee_password=xxxxx"
```

## Remove multiple (500) nodeJS apps
```
$ ansible-playbook helloapp_unbind.yml --extra-vars "apps_count=500 "
```