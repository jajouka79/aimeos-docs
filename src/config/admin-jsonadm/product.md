
# decorators
## excludes

Excludes decorators added by the "common" option from the JSON API clients

```
admin/jsonadm/product/decorators/excludes = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2016.01

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to remove a decorator added via
"admin/jsonadm/common/decorators/default" before they are wrapped
around the Jsonadm client.

```
 admin/jsonadm/decorators/excludes = array( 'decorator1' )
```

This would remove the decorator named "decorator1" from the list of
common decorators ("\Aimeos\Admin\JsonAdm\Common\Decorator\*") added via
"admin/jsonadm/common/decorators/default" for the JSON API client.

See also:

* admin/jsonadm/common/decorators/default
* admin/jsonadm/product/decorators/global
* admin/jsonadm/product/decorators/local

## global

Adds a list of globally available decorators only to the Jsonadm client

```
admin/jsonadm/product/decorators/global = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2016.01

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap global decorators
("\Aimeos\Admin\Jsonadm\Common\Decorator\*") around the Jsonadm
client.

```
 admin/jsonadm/product/decorators/global = array( 'decorator1' )
```

This would add the decorator named "decorator1" defined by
"\Aimeos\Admin\Jsonadm\Common\Decorator\Decorator1" only to the
"product" Jsonadm client.

See also:

* admin/jsonadm/common/decorators/default
* admin/jsonadm/product/decorators/excludes
* admin/jsonadm/product/decorators/local

## local

Adds a list of local decorators only to the Jsonadm client

```
admin/jsonadm/product/decorators/local = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2016.01

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap local decorators
("\Aimeos\Admin\Jsonadm\Product\Decorator\*") around the Jsonadm
client.

```
 admin/jsonadm/product/decorators/local = array( 'decorator2' )
```

This would add the decorator named "decorator2" defined by
"\Aimeos\Admin\Jsonadm\Product\Decorator\Decorator2" only to the
"product" Jsonadm client.

See also:

* admin/jsonadm/common/decorators/default
* admin/jsonadm/product/decorators/excludes
* admin/jsonadm/product/decorators/global