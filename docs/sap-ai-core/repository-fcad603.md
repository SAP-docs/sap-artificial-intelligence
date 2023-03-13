<!-- loiofcad60309cd24fe4a5f7534ed754a356 -->

# Repository



<a name="loiofcad60309cd24fe4a5f7534ed754a356__section_xhj_yqk_vsb"/>

## Repository `ra-aicore-test` not found for tenant

You get the result:

```
{
	"error":{
		"code": "500",
		"details": [
			{
				"code": null,
				"message": " "Repository ra-aicore-test not found for tenant b82a8318"
			}
		],
		"message": "Repository ra-aicore-test not found for tenant b82a8318"
		"request_id": null,
		"target": "/api/v4alpha/repositories"
	}
}
```

and:

```
AIAPIServerException: Failed to post /admin/repositories: Repository ra-aicore-test not found for tenant 68
```



### Follow the solution:

Use a different name for the value of the `name` parameter. The exception is raised by reuse of the name `aicore-test`.

```
response = ai_api_client.rest_clinet.post(
	path="/admin/repositories",
	body={
		"name": "aicore-test-1",
		"url": "https://github.com/John/aicore-test",
	}
)

print(response)

{'message': 'Repository has been on-boarded.'
```

**Parent topic:** [Troubleshooting](troubleshooting-3da90ba.md "For troubleshooting information, see the following sections:")

**Related Information**  


[Configuration](configuration-047fad5.md "")

[Artifacts](artifacts-c655daa.md "")

[Application](application-7f1e35b.md "")

[Execution](execution-5ccde4d.md "")

[Docker](docker-1945aa4.md "")

[Deployment](deployment-a10fa8a.md "")

[Miscellaneous](miscellaneous-10622b5.md "")

