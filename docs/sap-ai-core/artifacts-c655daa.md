<!-- loioc655daacecb94ef5a82ad5a1314788fb -->

# Artifacts



<a name="loioc655daacecb94ef5a82ad5a1314788fb__section_cn4_yqk_vsb"/>

## No output artifact has been generated



### Complete the following:

Define the `globalName` parameter for the output artifact in your workflow:

```
...
	executables.ai.sap.com/description: "Text classification Scikit training executable"
	executables.ai.sap.com/name: "text-clf-train-tutorial-exec"
	artifacts.ai.sap.com/text-data.kind: "dataset"
	artifacts.ai.sap.com/text-model-tutorial.kind: "mind"
labels:
	scenarios.ai.sap.com/id: "text-clf-tutorial"
	ai.sap.com/version: "2.1.0"
...
...
		outputs:
			artifacts:
				-name: text-model-tutorial
				path: /app/model
				global name: text-model-tutorial
				archive:
					none: {}
		container: 
...

```



<a name="loioc655daacecb94ef5a82ad5a1314788fb__section_q45_yqk_vsb"/>

## Failed to load artifacts: The specified key does not exist



### Complete the following:

1.  Ensure you have created an object store secret using the naming convention *<name\>* and the `pathPrefix` from your AWS S3 path. Refer to the following diagram:

    ![](images/solution11image1_d2bc541.png)

2.  When creating the artifact, don’t add the trailing forward slash \(/\) in URL parameter:
    -   Incorrect usage: `"url": "ai://yourObjectStoreSecretName/folder/subfolder/"`
    -   Correct usage: `"url": "ai://yourObjectStoreSecretName/folder/subfolder"`


**Parent topic:**[Troubleshooting](troubleshooting-3da90ba.md "For troubleshooting information, see the following sections:")

**Related Information**  


[Repository](repository-fcad603.md "")

[Configuration](configuration-047fad5.md "")

[Application](application-7f1e35b.md "")

[Execution](execution-5ccde4d.md "")

[Docker](docker-1945aa4.md "")

[Deployment](deployment-a10fa8a.md "")

[Miscellaneous](miscellaneous-10622b5.md "")

