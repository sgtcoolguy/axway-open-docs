{"title":"API Builder Secure Configuration at Rest","weight":"30"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

The API Builder configuration is stored on disk at rest. For example, connectors may store their usernames and passwords in the clear on disk. If the API Builder configuration contains sensitive information, storing the configuration on disk may cause a security concern. There are two relatively easy configuration options to avoid or mitigate the security concern:

* [Environment Configuration](#Environment) - Recommended for small teams or organizations

* [Encryption Configuration](#Encryption) - Recommended for larger teams or organizations


## Environment Configuration

One security configuration option is to remove the configuration settings from the API Builder configuration and retrieve them from the environment configuration. For example, to protect the salutation in the greetflow.default.js sample:

`module.exports = {`

`"helloworld"``: {`

`"salutation"``:` `"Howdy"`

`}`

`};`

Would become:

`module.exports = {`

`"helloworld"``: {`

`"salutation"``: process.env.SALUTATION`

`}`

`};`

When running locally, you can set the SALUTATION environment variable. Alternatively, you can hardcode the variable in the development configuration; but environmentalize it in the production configuration. When running in the cloud, you can set the variable on the deployed instance using the appc cloud config setting:

`appc cloud config --``set`  `"SALUTATION=Greetings"`

The same approach can be used to remove any sensitive settings from the API Builder configuration, such as connector passwords, and environmentalize them.

The environment configuration option requires cloud configuration updates any time a new variable is added or an existing one is changed. In small teams or organizations this may not be an issue, but in larger organizations tracking environment configuration changes could become unwanted overhead.

## Encryption Configuration

The second security configuration option is to keep the API Builder configuration settings on disk, but encrypt the configuration settings and keep the encryption key in the environment instead. The encrypted values are placed in the API Builder configuration in place of the clear text values. The following is one example of how this could be achieved; but there are many ways encrypting the sensitive API Builder configuration settings could be accomplished depending on security requirements.

1. Generate the encrypted value. The following example is a simple CLI that will AES encrypt a value passed in on the CLI:

  `const crypto = require(``'crypto'``);`

  `const algorithm =` `'aes256'``;`

  `const key = process.env.KEY ||` `'getKeyFromSomewhere'``;`

  `const cipherEncoding =` `'hex'``;`

  `const textEncoding =` `'utf-8'``;`

  `function` `encrypt(clearText) {`

  `const cipher = crypto.createCipher(algorithm, key)`

  `let cipherText = cipher.update(clearText, textEncoding, cipherEncoding)`

  `cipherText += cipher.final(cipherEncoding);`

  `return` `cipherText;`

  `}`

  `function` `decrypt(cipherText){`

  `const decipher = crypto.createDecipher(algorithm, key)`

  `let clearText = decipher.update(cipherText, cipherEncoding, textEncoding)`

  `clearText += decipher.final(textEncoding);`

  `return` `clearText;`

  `}`

  `const text = process.argv[2]`

  `const cipherText = encrypt(text)`

  ``console.log(`CIPHERTEXT: ${cipherText}`);``

  ``console.log(`CLEARTEXT: ${decrypt(cipherText)}`);``

  Encryption key:

  `$ node .``/crypt` `Hello`

  `CIPHERTEXT: 6b05e3830ba6638b0790a55cde19cdd7`

  `CLEARTEXT: Hello`

2. Place the encrypted value in the API Builder configuration. For this to work, API Builder must be able to decrypt the encrypted value. The decrypt function could be placed in a utility and used across multiple config files:

  `const crypto = require(``'crypto'``);`

  `const algorithm =` `'aes256'``;`

  `const key = process.env.KEY;`

  `function` `decrypt(cipherText){`

  `const decipher = crypto.createDecipher(algorithm, key)`

  `let clearText = decipher.update(cipherText,` `'hex'``,` `'utf-8'``)`

  `clearText += decipher.final(``'utf-8'``);`

  `return` `clearText;`

  `}`

  `module.exports = {`

  `"helloworld"``: {`

  `"salutation"``: decrypt(``'6b05e3830ba6638b0790a55cde19cdd7'``)`

  `}`

  `};`

3. Set the environment variable in the cloud using the encryption key:

  `appc cloud config --``set`  `"KEY=mySecretKey"`

  Now, when the application is published, API Builder will be able to decrypt the encrypted value.
