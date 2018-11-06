# Devtomic_Messages

![Magento 2.2 | 2.3](https://img.shields.io/badge/magento-2.2%20%7C%202.3-brightgreen.svg)
![Latest Stable Version](https://img.shields.io/packagist/v/devtomic/magento2-module-messages.svg)
![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)

![Devtomic](https://www.gravatar.com/avatar/1b69e38c54d6c7b0e0aa39c6189a7ec6?size=100)

The Messages module allows you to send success, notice, warning and error messages with HTML.

## Installation

```
composer require devtomic/magento2-module-messages
bin/magento module:enable Devtomic_Messages
bin/magento setup:upgrade
```

## Usage

Call the `addComplexSuccessMessage` function with the `withHtml` identifier. This identifer expects two arguments:

- `html`: A string containing the desired HTML
- `allowed_tags`: An array containing a list of strings of HTML tags to allow


## Demo

This code:

```
$this->messageManager->addComplexSuccessMessage(
    'withHtml',
    [
        'html' => '<b>This is bold text!</b> And this is not.',
        'allowed_tags' => ['b'],
    ]
);
```

Results in the following output:

![Screenshot](https://raw.githubusercontent.com/devtomic/magento2-module-messages/master/docs/demo.png)
