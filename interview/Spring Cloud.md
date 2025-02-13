When we talk about Spring Cloud, I'm referring to the canary release, which is a crucial requirement for our system.

Take our human resources management platform as an example. When there are changes in new tax policies or social security policies, we need to make corresponding changes to the system. At this time, we will adopt the canary release method to launch new services. 

The specific approach is as follows: When releasing a new service, we first specify the service version. For example, we set a new version and publish it to the Eureka registry. Then, at the gateway layer, we perform traffic routing. For instance, we direct 10% of the traffic to the new version of the service, while the remaining 90% of the traffic still goes to the original service.

However, if we use a random traffic allocation method, there may be a problem where the data requested for the first time is inconsistent with the data requested for the second time. Given that our platform is SaaS - based, we choose to route according to the different tenant IDs of different companies. 

For example, for some subsidiaries or companies in the testing phase, we will conduct canary tests on these companies first. The specific operation is to perform traffic distribution at the gateway layer, and we also use the configuration center here. In the configuration center, we specify the list of companies for canary testing. Through this list, we can dynamically control which companies can participate in the canary testing. This is one of our solutions.