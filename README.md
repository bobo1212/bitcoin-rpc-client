# A simple PHP client for bitcoin rpc.

## Installation with Composer

Add following lines to composer.json
```json
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/bobo1212/bitcoin-rpc-client.git"
        }
    ]
```

and run ```composer require bobo1212/bitcoin-rpc-client``` in your project directory.


## Table of Contents

- [Getting started](#getting-started)
- [How to send BTC](#How-to-send-btc)
- [Donations](#donations)
- [Contact](#contact)

## Getting started

```php
    /**
     * Include composer autoloader by uncommenting line below
     * if you're not already done it anywhere else in your project.
     **/
    // require 'vendor/autoload.php';
    
    $user = 'my_user_name';
    $password = 'my_password';
    $host = 'localhost';
    $port = 8332;
    
    $rpc = new \Bitcoin\RpcClient(
        $user,
        $password,
        $host,
        $port
    );
    
    $ret = $rpc->getbalances();
    
    if ($ret->error) {
        echo 'error: ' . $ret->error . "\n";
    } else {
        echo 'trusted: ' . $ret->result->mine->trusted . "\n";
        echo 'untrusted_pending: ' . $ret->result->mine->untrusted_pending . "\n";
        echo 'immature: ' . $ret->result->mine->immature . "\n";
    }
```
## How to send BTC
Send 0.0001 bitcoin to address 38kXJgKubEEojpzQe91T3dU6BKiwgN2euo:
```php

    $user = 'my_user_name';
    $password = 'my_password';
    $host = 'localhost';
    $port = 8332;
    
    $rpc = new \Bitcoin\RpcClient(
        $user,
        $password,
        $host,
        $port
    );
    
    $ret = $rpc->sendtoaddress('38kXJgKubEEojpzQe91T3dU6BKiwgN2euo', 0.0001);
    var_dump($ret);
```
Send 0.0001 BTC with a confirmation target of 6 blocks in economical fee estimate mode using positional arguments:
```php

    $user = 'my_user_name';
    $password = 'my_password';
    $host = 'localhost';
    $port = 8332;
    
    $rpc = new \Bitcoin\RpcClient(
        $user,
        $password,
        $host,
        $port
    );
    
    $ret = $rpc->sendtoaddress(
        '38kXJgKubEEojpzQe91T3dU6BKiwgN2euo',
        0.0001,
        'donation',
        "sean's outpost",
        false,
        true,
        6,
        'economical'
    );
    var_dump($ret);
```
## Donations
If you like this project, please consider donating:<br>
**BTC**: 38kXJgKubEEojpzQe91T3dU6BKiwgN2euo<br>
<p>
  <img src="assets/qrcode.png">
</p>
❤Thanks for your support!❤


## Contact
bobo1212@wp.pl