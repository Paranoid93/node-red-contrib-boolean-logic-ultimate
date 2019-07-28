# node-red-contrib-boolean-logic-ultimate

## DESCRIPTION
The node performs Boolean logic on the incoming payloads.<br/>
The node performs 3 checks (<b>AND,OR,XOR</b>) on the incoming boolean payloads and outputs the result at the same time, as follow:<br/>
- Output "AND": true or false<br/>
- Output "OR": true or false<br/>
- Output "XOR": true or false<br/>

The node can have a persistent input: the input values are retained after a node-red reboot. That means, that if you reboot your node-red, you don't need to wait all inputs to arrive and initialize the node, before the node can output a payload.

## CHANGELOG
* See <a href="https://github.com/Supergiovane/node-red-contrib-boolean-logic-ultimate/blob/master/CHANGELOG.md">here the changelog</a>

## CONFIGURATION
<p>
The node expects a fixed number of topics (configured in the settings) on which it will operate. It will only output a value 
when it has seen the expected number of topics. If it ever sees more than the configured number of topics it will log a message then reset its state and start over.<br/>
Changing the topic is usually only needed when chaining multiple boolean nodes after each other becuse the topics will then all be the same when delivered to the nodes further down the chain.<br/>
<br/>
<b>Filter output result</b><br />
<ol>	
    <li>Output both 'true' and 'false' results: Standard behaviour, the node will output <b>true</b> and <b>false</b> whenever it receives an input and calculate the boolean logics as output.</li>
    <li>Output only 'true' results: whenever the node receives an input, it outputs a payload <b>true</b> only if the result of the logic is true. <b>False</b> results are filtered out.</li>
</ol>
<br/>
<b>Remember latest input values after reboot</b><br />
If checked, the input values are retained after a node-red reboot. That means, that if you reboot your node-red, you don't need to wait all inputs to arrive and initialize the node, before the node can output a payload.<br/>
Every time you modify the node's config, <b>the retained values are cleared</b>.<br/>
<br/>
All incoming msg.payloads are converted into a boolean value according to the following rules (this applies to all boolean logic nodes):
<ol>	
    <li>Boolean values are taken as-is.</li>
    <li>For numbers, 0 evaluates to false, all other numbers evaluates to true.</li>
    <li>Strings are converted to numbers if they match the format of a decimal value, then the same rule as for numbers are applied. If it does not match, it evaluates to false. Also, the string "true" evaluates to true.</li>
</ol>
<br>
The XOR operation operates in a one, and only one mode, i.e. (A ^ B) ^ C ... ^ n
</p>