<!-- loio55d219794b5145b7b7c498a2b8fe7d3a -->

# Supported Parameters

The chat completions API supports a range of parameters that influence model responses, influencing aspects like creativity, length, and formatting of the output.



The following parameters are available:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

messages

</td>
<td valign="top">

array

</td>
<td valign="top">

Standard OpenAI chat completion format

</td>
</tr>
<tr>
<td valign="top">

model

</td>
<td valign="top">

string

</td>
<td valign="top">

Model identifier

</td>
</tr>
<tr>
<td valign="top">

frequency\_penalty

</td>
<td valign="top">

float

</td>
<td valign="top">

Penalize frequent tokens. Range: -2.0 to 2.0

</td>
</tr>
<tr>
<td valign="top">

presence\_penalty

</td>
<td valign="top">

float

</td>
<td valign="top">

Penalize frequent tokens. Range: -2.0 to 2.0

</td>
</tr>
<tr>
<td valign="top">

logit\_bias

</td>
<td valign="top">

map

</td>
<td valign="top">

Modify likelihood of specified tokens

</td>
</tr>
<tr>
<td valign="top">

max\_tokens

</td>
<td valign="top">

integer

</td>
<td valign="top">

Maximum tokens to generate

</td>
</tr>
<tr>
<td valign="top">

max\_completion\_tokens

</td>
<td valign="top">

integer

</td>
<td valign="top">

Maximum number of tokens that can be generated for a completion, including visible output tokens and reasoning tokens

</td>
</tr>
<tr>
<td valign="top">

n

</td>
<td valign="top">

integer

</td>
<td valign="top">

Number of completions to generate

</td>
</tr>
<tr>
<td valign="top">

presence\_penalty

</td>
<td valign="top">

float

</td>
<td valign="top">

Penalize new tokens based on presence. Range: -2.0 to 2.0

</td>
</tr>
<tr>
<td valign="top">

response\_format

</td>
<td valign="top">

object

</td>
<td valign="top">

Specify output format

</td>
</tr>
<tr>
<td valign="top">

stop

</td>
<td valign="top">

string or array

</td>
<td valign="top">

Stop sequences \(up to 4\)

</td>
</tr>
<tr>
<td valign="top">

stream

</td>
<td valign="top">

boolean

</td>
<td valign="top">

Enable streaming responses

</td>
</tr>
<tr>
<td valign="top">

temperature

</td>
<td valign="top">

float

</td>
<td valign="top">

Sampling temperature. Range: 0.0 to 2.0

</td>
</tr>
<tr>
<td valign="top">

top\_logprobs

</td>
<td valign="top">

integer

</td>
<td valign="top">

The number of most likely tokens to return at each token position, with corresponding log probability. Logprobs must be set to true if this parameter is used. Range: 0 to 20

</td>
</tr>
<tr>
<td valign="top">

logprobs

</td>
<td valign="top">

object

</td>
<td valign="top">

Whether to return log probabilities of the output tokens or not. True returns the log probabilities of each output token

</td>
</tr>
<tr>
<td valign="top">

top\_p

</td>
<td valign="top">

float

</td>
<td valign="top">

Nucleus sampling parameter. Range: 0.0 to 1.0

</td>
</tr>
<tr>
<td valign="top">

tools

</td>
<td valign="top">

array

</td>
<td valign="top">

List of tools the model may call

</td>
</tr>
<tr>
<td valign="top">

tool\_choice

</td>
<td valign="top">

string or object

</td>
<td valign="top">

Control tool calling strategy

</td>
</tr>
</table>

