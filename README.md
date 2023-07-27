# Spring-Boot-Profiles
It is a sample spring boot application which demonstrates the usage of different configuration for different environment via the use of profiles

Using multiple profiles in Spring Boot allows you to manage different deployment scenarios more easily and maintain separate configurations for each environment, making your application more flexible and adaptable across different setups.

For setting up different profiles, we can create YAML configuration files for each profile and let Spring Boot automatically pick the appropriate file based on the active profile.

_**By default, spring boot refers to the application.yaml file for its configuration (in which case the profile name is 'default')**_

---

In the ```src/main/resources``` folder, create separate **YAML** files for each profile you want to support. The naming convention for these files should be ```application-{profile}.yml```, where ```{profile}``` is the name of the profile (e.g., development, production, test, etc.).

For example:

- application-development.yml for the "development" profile
- application-production.yml for the "production" profile

---

Once the different profiles are ready, we need to specify an active profile which is done by means of the following property in application.yml file
```
spring:
    profiles:
        active: dev
```

---
We can also specify multiple profiles for the above property such that each one is separated by a comma. In this case, **_the application will then load the configurations from the specified profiles and override any shared properties based on the active profiles. If there are conflicts between the configurations of different profiles, the one specified in the last activated profile will take precedence._**
```
spring:
    profiles:
        active: dev, test, stage
```
