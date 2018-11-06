<h1 align="center">MarkShust_Messages</h1> 

<div align="center">
  <p>Send success, notice, warning and error messages with <code>&lt;html&gt;</code></p>
  
  <img src="https://img.shields.io/badge/magento-2.2%20|%202.3-brightgreen.svg?logo=magento&longCache=true&style=flat-square" alt="Supported Magento Versions" />
  <a href="https://packagist.org/packages/markshust/magento2-module-messages" target="_blank"><img src="https://img.shields.io/packagist/v/markshust/magento2-module-messages.svg?style=flat-square" alt="Latest Stable Version" /></a>
  <a href="https://packagist.org/packages/markshust/magento2-module-messages" target="_blank"><img src="https://poser.pugx.org/markshust/magento2-module-messages/downloads" alt="Composer Downloads" /></a>
  <a href="https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity" target="_blank"><img src="https://img.shields.io/badge/maintained%3F-yes-brightgreen.svg?style=flat-square" alt="Maintained - Yes" /></a>
  <a href="https://opensource.org/licenses/MIT" target="_blank"><img src="https://img.shields.io/badge/license-MIT-blue.svg" /></a>

</div>

## Table of contents

- [Summary](#summary)
- [Installation](#installation)
- [API](#api)
- [Usage](#usage)
- [License](#license)

## Summary

By default, when you call `$this->messageManager->addSuccessMessage` within Magento, you cannot pass custom HTML into your message. This doesn't provide you with the flexibility to provide customized messages to your visitors.

This module provides the ability to display custom messages including HTML, and still escapes the HTML to prevent cross-site scripting (XSS) attacks.

## Installation

```
composer require markshust/magento2-module-messages
bin/magento module:enable MarkShust_Messages
bin/magento setup:upgrade
```

## API

```php
/**
 * Any of the built-in complex message functions can be called with this identifer:
 *     addComplexSuccessMessage
 *     addComplexNoticeMessage
 *     addComplexWarningMessage
 *     addComplexErrorMessage
 * 
 * @param string $identifer Set to 'withHtml' to use this module.
 * @param mixed[] $data Data containing elements.
 *     @type string 'html' Desired output including HTML.
 *     @type string[] 'allowed_tags' (optional) List of allowed tags to render as HTML.
 */
$this->messageManager->addComplexSuccessMessage($identifer, $data);
```

## Usage

```php
protected messageManager;
 
public function __construct(
    ... 
    \Magento\Framework\Message\ManagerInterface $messageManager,
    ...
) {
    $this->messageManager = $messageManager;
    ...
}

$this->messageManager->addComplexSuccessMessage('withHtml', [
    'html' => '<b>This is bold text!</b> And this is not.',
    'allowed_tags' => ['b'],
]);
```

![Screenshot](https://raw.githubusercontent.com/markshust/magento2-module-messages/master/docs/demo.png)

## License

[MIT](https://opensource.org/licenses/MIT)
