<!-- loioa10fa8a7f3144d25a2a6ddee72d311a2 -->

# Deployment



<a name="loioa10fa8a7f3144d25a2a6ddee72d311a2__section_wqn_yqk_vsb"/>

## You want to force a deployment with status UNKNOWN to stop

You want to stop and delete a deployment but you are unable to because the deployment status is “Unknown”. You have tried to submit a PATCH request as follows:

***PATCH***`{{apiurl}}/lm/deployments/d4fec9c24c54f87e`

However, you receive the following response:

```

{
	"error": {
		"code": "01010076"
		"message": "Invalid Request, Current status UNKNOWN cannot be changed..",
		"requestID": "e110820e-1cfe-456a-bb0e-77907b36422c",
		"target": "/apu/v2/deployments/d4fec9c24c54f87e"
	}
```



### Complete the following steps:

1.  Find out why your deployment status is “Unknown” by using the endpoint:

    ***GET*** `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`

2.  Delete the deployment without trying to stop it \(stopping a deployment is necessary only when it's running\):

    ***DELETE*** `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`




<a name="loioa10fa8a7f3144d25a2a6ddee72d311a2__section_qwq_yqk_vsb"/>

## Deployment remains in status PENDING



### Check the following:

1.  Check that the Docker Registry secret exists when using your private Docker Image.
2.  Check that your Docker Image can be downloaded to your local system.



<a name="loioa10fa8a7f3144d25a2a6ddee72d311a2__section_f5w_xlr_xsb"/>

## Deployment ID *<abc\>* not found

This message appears when you have just started the deployment. Wait a few minutes and the message will resolve itself automatically.

**Parent topic:** [Troubleshooting](troubleshooting-3da90ba.md "For troubleshooting information, see the following sections:")

**Related Information**  


[Repository](repository-fcad603.md "")

[Configuration](configuration-047fad5.md "")

[Artifacts](artifacts-c655daa.md "")

[Application](application-7f1e35b.md "")

[Execution](execution-5ccde4d.md "")

[Docker](docker-1945aa4.md "")

[Miscellaneous](miscellaneous-10622b5.md "")

