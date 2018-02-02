
Add PCF environment variables
export PCF_API=xxxx
export PCF_ORG=xxx
export PCF_SPACE=xxx
export PCF_DOMAIN=xxx
export APIGEE_ORG=xxx
export APIGEE_ENV=xxx

Login PCF
$ cf login $PCF_DOMAIN --skip-ssl-validation

Create multiple nodeJS apps
$ ansible-playbook helloapp.yml