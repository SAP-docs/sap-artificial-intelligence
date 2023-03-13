<!-- loio185a3245692542a78bfeff87220410c6 -->

# Consume Generic Secrets in Executions or Deployments

Utilize generic secrets in executions or deployments.

Generic secrets at resource-group level can be attached to containers in executions or deployments. They can either be mounted as a volume or attached as an environment variable. The following examples illustrate how to consume a generic secret in a container by declaring it in the template. Note that only generic secrets can be attached to containers in this way. Any nongeneric secret cannot be consumed in a template.



<a name="loio185a3245692542a78bfeff87220410c6__section_mjm_b1l_4rb"/>

## Consume a Generic Secret as an Environment Variable

Generic secrets can be attached to containers using either `envFrom.secretRef` or `env.valueFrom.secretKeyRef`, as shown below.

-   Using `envFrom.secretRef`:

    ```
    spec:
    	containers:
    	- name: my-kserve-container
    		image: centaur
    		envFrom:
    		- secretRef:
    			name: my-generic-secret					
    ```

-   Using `env.valueFrom.secretKeyRef`:

    ```
    spec:
    	containers:
    	- name: kserve-container
    		image: centaur
    		env:
    		- name: MY_GENERIC_SECRET
    		  valueFrom:
    			secretKeyRef:
    				name: my-generic-secret
    				key: some-credential
    ```




<a name="loio185a3245692542a78bfeff87220410c6__section_gbm_1cl_4rb"/>

## Consume a Generic Secret as a Volume Mount

Generic secrets can also be mounted to containers as volumes, as shown below.

```
spec:
	containers:
		- name: kserve-container
		image: centaur	
		volumeMounts:
			- name: my-generic-secret
			  mountPath: "/etc/my-generic-secret"
			  readOnly: true
	volumes:
		- name: my-generic-secret
		  secret:
			secretName: my-generic-secret
```



<a name="loio185a3245692542a78bfeff87220410c6__section_eqj_2cl_4rb"/>

## Additional Information

Secret names can be parameterized in the templates and supplied via AI API configurations, as shown below.

```
envFrom:
- secretRef:
  name: "{{inputs.parameters.secretName}}"					
```

**Parent topic:** [Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group represents a unique workspace environment, where users can create or add entities such as configurations, executions, deployments, and artifacts.")

**Related Information**  


[Create a Resource Group](create-a-resource-group-01753f4.md "You can create resource groups to isolate ML workloads.")

[Create a Generic Secret](create-a-generic-secret-1831845.md "A generic secret gives SAP AI Core authorization to utilize your resource group without exposing your credentials.")

[List All Generic Secrets](list-all-generic-secrets-05a3713.md "Locate a generic secret, without revealing sensitive information.")

[Update a Generic Secret](update-a-generic-secret-b5d5970.md "Generic secrets can be amended.")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "Manage the lifespan of your generic secrets.")

