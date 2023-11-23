<!-- loio185a3245692542a78bfeff87220410c6 -->

# Consume Generic Secrets in Executions or Deployments

Generic secrets at resource-group level can be attached to containers in executions or deployments. They can either be mounted as a volume or attached as an environment variable. The following examples illustrate how to consume a generic secret in a container by declaring it in the template. Note that only generic secrets can be attached to containers in this way. System secrets cannot be consumed in a template.



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
    			name: MY_GENERIC_SECRET					
    ```

    If your secret contains invalid characters, such as hyphens \(-\), this method will result in error. You will need to map your secret to a valid variable name using `env.valueFrom.secretKeyRef`.

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

Secret names can be included as parameters in the templates and supplied via AI API configurations, as shown below.

```
envFrom:
- secretRef:
  name: "{{inputs.parameters.secretName}}"					
```

