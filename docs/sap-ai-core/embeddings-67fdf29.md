<!-- loio67fdf29b483042d49e26c7970336bc3a -->

# Embeddings

Semantic embeddings are multidimensional representations of textual information.

The embeddings endpoint is harmonized across different LLMs and can be used alone, or with anonymization of input data.

For more information about supported models, see references to orchestration in [Supported Models](supported-models-509e588.md).

Send POST request to the endpoint `{{Orchestration URL}}/v2/embeddings` and populate the sample code with the following values:


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

\{\{orchestration-deployment-url\}\}

</td>
<td valign="top">

The URL of your RUNNING orchestration deployment.

</td>
</tr>
<tr>
<td valign="top">

\{\{token\}\}

</td>
<td valign="top">

Your authorization token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

\{\{resource\_group\}\}

</td>
<td valign="top">

The AI resource group assigned to your account

</td>
</tr>
</table>



<a name="loio67fdf29b483042d49e26c7970336bc3a__section_axz_3gf_xfc"/>

## Minimal Call

The following minimal call shows a model selection and input text.

```
curl --request POST \
  --url {{Orchestration URL}}/v2/embeddings \
  --header 'AI-Resource-Group: {{resource group}}' \
  --header 'Authorization: Bearer {{token}}' \
  --header 'content-type: application/json' \
  --data '{
  "config": {
    "modules": {
      "embeddings": {
        "model": {
          "name": "text-embedding-3-large"
        }
      }
    }
  },
  "input": {
    "text": "Hello, SAP!"
  }
}'
```



<a name="loio67fdf29b483042d49e26c7970336bc3a__section_oh2_4gf_xfc"/>

## Module Calling

The following example includes model parameters and masking configuration. For more information, see [Data Masking](data-masking-8b87002.md) and [Model Configuration](model-configuration-c1bdb26.md).

```
curl --request POST \
  --url {{Orchestration URL}}/v2/embeddings \
  --header 'AI-Resource-Group: {{resource group}}' \
  --header 'Authorization: Bearer {{token}}' \
  --header 'content-type: application/json' \
  --data '{
  "config": {
    "modules": {
      "embeddings": {
        "model": {
          "name": "text-embedding-3-large",
          "version": "latest",
          "params": {
            "encoding_format": "float",
            "dimensions": 5
          }
        }
      },
      "masking": {
        "masking_providers": [
          {
            "type": "sap_data_privacy_integration",
            "method": "anonymization",
            "entities": [
              {
                "type": "profile-person"
              },
              {
                "type": "profile-email"
              },
              {
                "type": "profile-phone"
              },
              {
                "type": "profile-nationality"
              },
              {
                "type": "profile-university"
              },
              {
                "type": "profile-location"
              },
              {
                "type": "profile-url"
              },
              {
                "type": "profile-gender"
              },
              {
                "type": "profile-credit-card-number"
              }
            ]
          }
        ]
      }
    }
  },
  "input": {
    "text": "Hello, Jake! I had a great meeting with the English stakeholder from Oxford University, located at 1 Infinite Loop, London. They left their contacts: manufacturer@gmail.com, or we may call them via +49 1522 3433333 . Their organization, SAP Public, provided the following details: National ID 123456789, IBAN DE89370400440532013000, SSN 987-65-4320, passport number X1234567, and credit card number 4111 1111 1111 1111. Their gender is male, nationality is British, and their political group is Green Party. For more info, visit https://sap.com or use the username: jake_user and password: SuperSecret123!",
    "type": "text"
  }
}'
```

