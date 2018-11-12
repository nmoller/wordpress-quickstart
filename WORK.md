# Openshift usage

On veut répartir avec le projet clean:
```
oc delete all --all
# Output
pod "moodle-1-build" deleted
pod "moodle-2-build" deleted
pod "moodle-3-build" deleted
pod "moodle-3-c5wd8" deleted
pod "moodle-4-build" deleted
pod "moodle-5-build" deleted
pod "moodle-6-build" deleted
pod "moodle-7-build" deleted
pod "my-wordpress-site-1-build" deleted
pod "my-wordpress-site-2-67mzh" deleted
pod "my-wordpress-site-db-1-pc8kk" deleted
pod "mysql-1-5f5qd" deleted
pod "redis-1-92dc9" deleted
replicationcontroller "moodle-1" deleted
replicationcontroller "moodle-2" deleted
replicationcontroller "moodle-3" deleted
replicationcontroller "my-wordpress-site-1" deleted
replicationcontroller "my-wordpress-site-2" deleted
replicationcontroller "my-wordpress-site-db-1" deleted
replicationcontroller "mysql-1" deleted
replicationcontroller "redis-1" deleted
service "moodle" deleted
service "my-wordpress-site" deleted
service "my-wordpress-site-db" deleted
service "mysql" deleted
service "redis" deleted
deploymentconfig.apps.openshift.io "moodle" deleted
deploymentconfig.apps.openshift.io "my-wordpress-site" deleted
deploymentconfig.apps.openshift.io "my-wordpress-site-db" deleted
deploymentconfig.apps.openshift.io "mysql" deleted
deploymentconfig.apps.openshift.io "redis" deleted
buildconfig.build.openshift.io "moodle" deleted
buildconfig.build.openshift.io "my-wordpress-site" deleted
build.build.openshift.io "moodle-1" deleted
build.build.openshift.io "moodle-2" deleted
build.build.openshift.io "moodle-3" deleted
build.build.openshift.io "moodle-4" deleted
build.build.openshift.io "moodle-5" deleted
imagestream.image.openshift.io "moodle" deleted
imagestream.image.openshift.io "my-wordpress-site-img" deleted
route.route.openshift.io "moodle" deleted
route.route.openshift.io "my-wordpress-site" deleted
```

Les pvc n'ont pas été effacées, on le fait:
```
oc get pvc
...
```

L'adresse est `https://192.168.42.139:8443`

### Structure du template

```
cat templates/classic-standalone.yaml |grep kind
kind: Template
  kind: ImageStream
  kind: BuildConfig
        kind: ImageStreamTag
          kind: ImageStreamTag
  kind: DeploymentConfig
          kind: ImageStreamTag
  kind: DeploymentConfig
          kind: ImageStreamTag
  kind: Service
  kind: Service
  kind: Route
      kind: Service
  kind: PersistentVolumeClaim
  kind: PersistentVolumeClaim
```