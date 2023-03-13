<!-- loio66413f1d9fbf4758a0d739eaf1c95dc7 -->

# Create Artifacts

Create an artifact to connect a dataset or model, to make it available for use in SAP AI Core.



<a name="loio66413f1d9fbf4758a0d739eaf1c95dc7__section_rtq_mxp_brb"/>

## Using Postman

1.  Create a new ***POST*** request using URL `{{apiurl}}/v2/lm/artifacts`
2.  Toggle the body tab, and enter the following JSON:

    ```
    {
      "name": "name of artifact",
      "kind": "dataset",
      "url": "ai://<objectStore name>/<data path>",
      "description": "<description of artifact>",
      "scenarioId": "<scenarioID>"
    }
    ```

    > ### Note:  
    > The `objectStore name`, `data path` and `scenarioId` refer to pre-existing values.


The response body contains the ID of your new artifact.

```
{
    "id": "3x4mpl3-651c-4f3e-8e1d-81a408041bc1",
    "message": "Artifact acknowledged",
    "url": "ai://default/data"
}
```



<a name="loio66413f1d9fbf4758a0d739eaf1c95dc7__section_shh_nxp_brb"/>

## Using curl

```
curl --location --request POST "[/pandoc/div/div/horizontalrule/codeblock/span/code
     {"filepath"}) $API_URL/v2/lm/artifacts (code]" \
--header "Authorization: Bearer $TOKEN" \
--header "Content-Type: application/json" \
--header "AI-Resource-Group: <Resource group>" \
--data-raw '{
   "name": "name of artifact",
   "kind": "dataset",
   "url": "ai://<objectStore name>/<data path>",
   "description": "<description of artifact>",
   "scenarioId": "<scenarioID>"
}
```

> ### Note:  
> The `objectStore name`, `data path` and `scenarioId` refer to pre-existing values.

The response body contains the ID of your new artifact.

```
{
    "id": "3x4mpl3-651c-4f3e-8e1d-81a408041bc1",
    "message": "Artifact acknowledged",
    "url": "ai://default/data"
}
```

**Parent topic:** [Manage Artifacts](manage-artifacts-386ba71.md "An artifact is a reference to data or a file that is produced or consumed by an execution or deployment. They are managed through SAP AI Core and your connected object store.")

**Related Information**  


[List Artifacts](list-artifacts-1d613e0.md "Retrieve a list of existing artifacts.")

