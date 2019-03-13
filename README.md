# Point Type
Point Type to Doctrine2

[![Build Status](https://travis-ci.org/vinyvicente/doctrine-point-type.svg?branch=master)](https://travis-ci.org/vinyvicente/doctrine-point-type)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/vinyvicente/doctrine-point-type/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/vinyvicente/doctrine-point-type/?branch=master)
[![Latest Stable Version](https://poser.pugx.org/vinyvicente/doctrine-point-type/v/stable)](https://packagist.org/packages/vinyvicente/doctrine-point-type)
[![Total Downloads](https://poser.pugx.org/vinyvicente/doctrine-point-type/downloads)](https://packagist.org/packages/vinyvicente/doctrine-point-type)
[![License]]



### Versions:

| Version  |  PHP Version |
|---|---|
| 1.*  |  7.0 |
| 2.*  |  7.1 or higher |


## How to use

First, composer install:

```
composer require vinyvicente/doctrine-point-type
```

After, add in your bootstrap:


```php
use Doctrine\DBAL\Types\Type;

$em = YourEntityManager();

Type::addType('point', 'Viny\PointType');

// in case silex :)
$em->getConnection()->getDatabasePlatform()->registerDoctrineTypeMapping('point', 'point');

```

Or add it in your app/config yml files
```
doctrine:
    dbal:
        types:
            point: Viny\PointType
        default_connection: default
        connections:
            default:
                driver: pdo_mysql
                host: '%database_host%'
                port: '%database_port%'
                dbname: '%database_name%'
                user: '%database_user%'
                password: '%database_password%'
                charset: UTF8
                mapping_types:
                    point: point
```

## Exclusive to symfony 4

In your controller, below the namespace, call the file

```<?php
namespace App\Controller;

use Josue\Point;
use App\Entity\GeoLocation;

```
In your entity create a point type file
```/**
   *  
   * @ORM\Column(name="GeoLocation", type="point")
   */
   private $GeoLocation;
   
   public function getGeoLocation()
   {
       return $this->GeoLocation;
   }
   public function setGeoLocation($GeoLocation)
   {
      $this->GeoLocation = $GeoLocation;
      return $this;
   }
```

You should now configure your file doctrine.yaml
``` doctrine:
    dbal:
        types:
            point: Josue\PointType
        mapping_types:
            point: point
```

### Now it's just enjoy, and good young work!!!
