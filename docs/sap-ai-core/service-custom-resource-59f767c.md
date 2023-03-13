<!-- loio59f767c1874f4b46b6c55e93c0b1e900 -->

# Service Custom Resource

The service provider main tenant needs to prepare the service custom resource. The custom resource contains service details, reference to broker credentials or secrets, and capabilities configured for service consumers.

An example service custom resource is provided in the following code block:

```

apiVersion: ai.sap.com/v1alpha1
kind: Service
metadata:
	name: sample-service
spec:
	brokerSecret:
		name: broker-credentials
		usernameKeyRef: username
		passwordKeyRef: password
	description: Service used for demos
	capabilities:
		basic:
			staticDeployments: true
			userDeployments: true
			createExecutions: true
		logs:
			executions: true
			deployments: true
	serviceCatalog:
	- extendCredentials:
		shared:
			serviceUrls:
				AI_SVC_URL: https://api.ai.internalprod.eu-central-1.aws.ml.hana.ondemand.com
	extendCatalog:
		name: sample-service
		id: sample-service-broker-id
		description: sample service
		bindable: true
		plans:
			- id: sample-service-standard
			description: Standard plan for sample service
			name: standard
			free: false					
			metadata:
				supportedPlatforms:
				- cloudfoundry
				- kubernetes
				- sapbtp

```

This can be used as a guide, with values amended as required. To create YAML descriptors, use any text editor with a YAML plugin.

For details about parameters, refer to the following table:

**Service Parameter Details**


<table>
<tr>
<th valign="top">

Type



</th>
<th valign="top" colspan="2">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

metadata



</td>
<td valign="top" colspan="2">

name



</td>
<td valign="top">

Name for the service



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

brokerSecret



</td>
<td valign="top" colspan="2">

name



</td>
<td valign="top">

Secret’s name containing credentials to register Service Broker.

> ### Note:  
> It is mandatory to have this secret registered as a generic secret.



</td>
</tr>
<tr>
<td valign="top" colspan="2">

usernameKeyRef



</td>
<td valign="top">

Key reference for username from registered Secret.



</td>
</tr>
<tr>
<td valign="top" colspan="2">

passwordKeyRef



</td>
<td valign="top">

Key reference for password from registered Secret.



</td>
</tr>
<tr>
<td valign="top" rowspan="5">

capabilities



</td>
<td valign="top" rowspan="3">

basic



</td>
<td valign="top">

staticDeployments



</td>
<td valign="top">

Static global inference endpoints without the need of user deployments \(default: true\).



</td>
</tr>
<tr>
<td valign="top">

userDeployments



</td>
<td valign="top">

Consumers can create deployments \(default: true\).



</td>
</tr>
<tr>
<td valign="top">

createExecutions



</td>
<td valign="top">

Consumers can create executions \(default: true\).



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

logs



</td>
<td valign="top">

executions



</td>
<td valign="top">

Consumers can access execution logs.



</td>
</tr>
<tr>
<td valign="top">

deployments



</td>
<td valign="top">

Consumers can access deployment logs.



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

serviceCatalog



</td>
<td valign="top" colspan="2">

extendCredentials



</td>
<td valign="top">

Used to mention to be consumed Service URL. It will reflect in the service-key.



</td>
</tr>
<tr>
<td valign="top" colspan="2">

extendCatalog



</td>
<td valign="top">

Used to extend service catalog.



</td>
</tr>
</table>

