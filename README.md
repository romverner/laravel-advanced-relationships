Laravel Advanced Relationships
==============

Multi-column and JSON-column relationships for Laravel Eloquent using [awobaz/compoships](https://github.com/topclaudy/compoships) and [staudenmeir/eloquent-json-relations](https://github.com/staudenmeir/eloquent-json-relations)

In a recent project, I've encountered the need to use both multi-column and JSON-column relationships in the same model. Neither functionality is supported natively by Laravel. Two third-party packages exist that provide these functionalities separately, however, they have several conflicting methods so they can't be used together in the same class. This package combines [awobaz/compoships](https://github.com/topclaudy/compoships) and [staudenmeir/eloquent-json-relations](https://github.com/staudenmeir/eloquent-json-relations) to provide full functionality of both in the same Laravel model.

## Notice
This is a forked version of the original package sheldonreiff/laravel-advanced-relationships, which was created to work with Laravel 5. I created the dev-master branch here to work with Laravel 8.

## Installation
```
If using Laravel 5-7, please use the original package originally created by sheldonreiff:
    composer require romverner/laravel-advanced-relationships

If using Laravel 8, please use the updated package:
    composer require romverner/laravel-advanced-relationships:dev-master
```

## Usage
Add the `HasAdvancedRelationships` trait to both the parent and the related model. For all of the supported relationships, either a JSON column, multiple columns, or multiple JSON columns may be specified for the local and foreign keys as seen in the example below.

```
namespace App;

use Illuminate\Database\Eloquent\Model;

class A extends Model
{
    use \Reiff\AdvancedRelationships\HasAdvancedRelationships;
    
    public function b()
    {
        return $this->hasMany('B', 'f1', 'details->l1');
    }
    
    public function c()
    {
        return $this->hasMany('C', ['f1', 'details->f2'], ['details->l1', 'l2']);
    }
}
```

## Supported relationships
Both multi-column and JSON-column support are provided for the following relationships.
- hasOne
- hasMany
- belongsTo

## Additional information
Refer to [awobaz/compoships](https://github.com/topclaudy/compoships) and [staudenmeir/eloquent-json-relations](https://github.com/staudenmeir/eloquent-json-relations) for additional functionality and other information. This package depends on these packages and simply implements the necessary integrations to make them work together.
