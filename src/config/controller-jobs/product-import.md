
# csv
## backup

Name of the backup for sucessfully imported files

```
controller/jobs/product/import/csv/backup = backup-%Y-%m-%d.csv
```

* Default: 
* Type: integer - Name of the backup file, optionally with date/time placeholders
* Since: 2018.04

After a CSV file was imported successfully, you can move it to another
location, so it won't be imported again and isn't overwritten by the
next file that is stored at the same location in the file system.

You should use an absolute path to be sure but can be relative path
if you absolutely know from where the job will be executed from. The
name of the new backup location can contain placeholders understood
by the PHP DateTime::format() method (with percent signs prefix) to
create dynamic paths, e.g. "backup/%Y-%m-%d" which would create
"backup/2000-01-01". For more information about the date() placeholders,
please have a look  into the PHP documentation of the
[format() method](https://www.php.net/manual/en/datetime.format.php).

**Note:** If no backup name is configured, the file will be removed!

See also:

* controller/jobs/product/import/csv/domains
* controller/jobs/product/import/csv/location
* controller/jobs/product/import/csv/mapping
* controller/jobs/product/import/csv/max-size
* controller/jobs/product/import/csv/skip-lines

## decorators/excludes

Excludes decorators added by the "common" option from the product import CSV job controller

```
controller/jobs/product/import/csv/decorators/excludes = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2015.01

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to remove a decorator added via
"controller/jobs/common/decorators/default" before they are wrapped
around the job controller.

```
 controller/jobs/product/import/csv/decorators/excludes = array( 'decorator1' )
```

This would remove the decorator named "decorator1" from the list of
common decorators ("\Aimeos\Controller\Jobs\Common\Decorator\*") added via
"controller/jobs/common/decorators/default" to the job controller.

See also:

* controller/jobs/common/decorators/default
* controller/jobs/product/import/csv/decorators/global
* controller/jobs/product/import/csv/decorators/local

## decorators/global

Adds a list of globally available decorators only to the product import CSV job controller

```
controller/jobs/product/import/csv/decorators/global = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2015.01

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap global decorators
("\Aimeos\Controller\Jobs\Common\Decorator\*") around the job controller.

```
 controller/jobs/product/import/csv/decorators/global = array( 'decorator1' )
```

This would add the decorator named "decorator1" defined by
"\Aimeos\Controller\Jobs\Common\Decorator\Decorator1" only to the job controller.

See also:

* controller/jobs/common/decorators/default
* controller/jobs/product/import/csv/decorators/excludes
* controller/jobs/product/import/csv/decorators/local

## decorators/local

Adds a list of local decorators only to the product import CSV job controller

```
controller/jobs/product/import/csv/decorators/local = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2015.01

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap local decorators
("\Aimeos\Controller\Jobs\Product\Import\Csv\Decorator\*") around the job
controller.

```
 controller/jobs/product/import/csv/decorators/local = array( 'decorator2' )
```

This would add the decorator named "decorator2" defined by
"\Aimeos\Controller\Jobs\Product\Import\Csv\Decorator\Decorator2"
only to the job controller.

See also:

* controller/jobs/common/decorators/default
* controller/jobs/product/import/csv/decorators/excludes
* controller/jobs/product/import/csv/decorators/global

## domains

List of item domain names that should be retrieved along with the product items

```
controller/jobs/product/import/csv/domains = Array
(
    [attribute] => attribute
    [catalog] => catalog
    [media] => media
    [price] => price
    [product] => product
    [product/property] => product/property
    [supplier] => supplier
    [text] => text
)
```

* Default: Array
(
)

* Type: array - Associative list of MShop item domain names
* Since: 2018.04

For efficient processing, the items associated to the products can be
fetched to, minimizing the number of database queries required. To be
most effective, the list of item domain names should be used in the
mapping configuration too, so the retrieved items will be used during
the import.

See also:

* controller/jobs/product/import/csv/backup
* controller/jobs/product/import/csv/location
* controller/jobs/product/import/csv/mapping
* controller/jobs/product/import/csv/max-size
* controller/jobs/product/import/csv/skip-lines

## location

File or directory where the content is stored which should be imported

```
controller/jobs/product/import/csv/location = product
```

* Default: product
* Type: string - Relative path to the CSV files
* Since: 2015.08

You need to configure the CSV file or directory with the CSV files that
should be imported. It should be an absolute path to be sure but can be
relative path if you absolutely know from where the job will be executed
from.

See also:

* controller/jobs/product/import/csv/backup
* controller/jobs/product/import/csv/domains
* controller/jobs/product/import/csv/location
* controller/jobs/product/import/csv/mapping
* controller/jobs/product/import/csv/max-size
* controller/jobs/product/import/csv/skip-lines

## mapping

List of mappings between the position in the CSV file and item keys

```
controller/jobs/product/import/csv/mapping = Array
(
    [item] => Array
        (
            [0] => product.code
            [1] => product.label
            [2] => product.type
            [3] => product.status
        )

    [text] => Array
        (
            [4] => text.type
            [5] => text.content
            [6] => text.type
            [7] => text.content
        )

    [media] => Array
        (
            [8] => media.url
        )

    [price] => Array
        (
            [9] => price.currencyid
            [10] => price.quantity
            [11] => price.value
            [12] => price.taxrate
        )

    [attribute] => Array
        (
            [13] => attribute.code
            [14] => attribute.type
        )

    [product] => Array
        (
            [15] => product.code
            [16] => product.lists.type
        )

    [property] => Array
        (
            [17] => product.property.value
            [18] => product.property.type
        )

    [catalog] => Array
        (
            [19] => catalog.code
            [20] => catalog.lists.type
        )

)
```

* Default: Array
(
    [item] => Array
        (
            [0] => product.code
            [1] => product.label
            [2] => product.type
            [3] => product.status
        )

    [text] => Array
        (
            [4] => text.type
            [5] => text.content
            [6] => text.type
            [7] => text.content
        )

    [media] => Array
        (
            [8] => media.url
        )

    [price] => Array
        (
            [9] => price.currencyid
            [10] => price.quantity
            [11] => price.value
            [12] => price.taxrate
        )

    [attribute] => Array
        (
            [13] => attribute.code
            [14] => attribute.type
        )

    [product] => Array
        (
            [15] => product.code
            [16] => product.lists.type
        )

    [property] => Array
        (
            [17] => product.property.value
            [18] => product.property.type
        )

    [catalog] => Array
        (
            [19] => catalog.code
            [20] => catalog.lists.type
        )

)

* Type: array - Associative list of processor names and lists of key/position pairs
* Since: 2018.04

The importer have to know which data is at which position in the CSV
file. Therefore, you need to specify a mapping between each position
and the MShop domain item key (e.g. "product.code") it represents.

You can use all domain item keys which are used in the fromArray()
methods of the item classes.

These mappings are grouped together by their processor names, which
are responsible for importing the data, e.g. all mappings in "item"
will be processed by the base product importer while the mappings in
"text" will be imported by the text processor.

See also:

* controller/jobs/product/import/csv/backup
* controller/jobs/product/import/csv/domains
* controller/jobs/product/import/csv/location
* controller/jobs/product/import/csv/max-size
* controller/jobs/product/import/csv/skip-lines

## max-size

Maximum number of CSV rows to import at once

```
controller/jobs/product/import/csv/max-size = 1000
```

* Default: 1000
* Type: integer - Number of rows
* Since: 2018.04

It's more efficient to read and import more than one row at a time
to speed up the import. Usually, the bigger the chunk that is imported
at once, the less time the importer will need. The downside is that
the amount of memory required by the import process will increase as
well. Therefore, it's a trade-off between memory consumption and
import speed.

See also:

* controller/jobs/product/import/csv/backup
* controller/jobs/product/import/csv/domains
* controller/jobs/product/import/csv/location
* controller/jobs/product/import/csv/mapping
* controller/jobs/product/import/csv/skip-lines

## name

Class name of the used product suggestions scheduler controller implementation

```
controller/jobs/product/import/csv/name = 
```

* Default: 
* Type: string - Last part of the class name
* Since: 2015.01

Each default job controller can be replace by an alternative imlementation.
To use this implementation, you have to set the last part of the class
name as configuration value so the controller factory knows which class it
has to instantiate.

For example, if the name of the default class is

```
 \Aimeos\Controller\Jobs\Product\Import\Csv\Standard
```

and you want to replace it with your own version named

```
 \Aimeos\Controller\Jobs\Product\Import\Csv\Mycsv
```

then you have to set the this configuration option:

```
 controller/jobs/product/import/csv/name = Mycsv
```

The value is the last part of your own class name and it's case sensitive,
so take care that the configuration value is exactly named like the last
part of the class name.

The allowed characters of the class name are A-Z, a-z and 0-9. No other
characters are possible! You should always start the last part of the class
name with an upper case character and continue only with lower case characters
or numbers. Avoid chamel case names like "MyCsv"!


## skip-lines

Number of rows skipped in front of each CSV files

```
controller/jobs/product/import/csv/skip-lines = 1
```

* Default: 0
* Type: integer - Number of rows
* Since: 2015.08

Some CSV files contain header information describing the content of
the column values. These data is for informational purpose only and
can't be imported into the database. Using this option, you can
define the number of lines that should be left out before the import
begins.

See also:

* controller/jobs/product/import/csv/backup
* controller/jobs/product/import/csv/domains
* controller/jobs/product/import/csv/location
* controller/jobs/product/import/csv/mapping
* controller/jobs/product/import/csv/max-size

# xml
## backup

Name of the backup for sucessfully imported files

```
controller/jobs/product/import/xml/backup = 
```

* Default: 
* Type: integer - Name of the backup file, optionally with date/time placeholders
* Since: 2019.04

After a XML file was imported successfully, you can move it to another
location, so it won't be imported again and isn't overwritten by the
next file that is stored at the same location in the file system.

You should use an absolute path to be sure but can be relative path
if you absolutely know from where the job will be executed from. The
name of the new backup location can contain placeholders understood
by the PHP DateTime::format() method (with percent signs prefix) to
create dynamic paths, e.g. "backup/%Y-%m-%d" which would create
"backup/2000-01-01". For more information about the date() placeholders,
please have a look  into the PHP documentation of the
[format() method](https://www.php.net/manual/en/datetime.format.php).

**Note:** If no backup name is configured, the file will be removed!

See also:

* controller/jobs/product/import/xml/domains
* controller/jobs/product/import/xml/location
* controller/jobs/product/import/xml/max-query

## decorators/excludes

Excludes decorators added by the "common" option from the product import CSV job controller

```
controller/jobs/product/import/xml/decorators/excludes = Array
(
)
```

* Default: Array
(
)

* Type: array - List of decorator names
* Since: 2019.04

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to remove a decorator added via
"controller/jobs/common/decorators/default" before they are wrapped
around the job controller.

```
 controller/jobs/product/import/xml/decorators/excludes = array( 'decorator1' )
```

This would remove the decorator named "decorator1" from the list of
common decorators ("\Aimeos\Controller\Jobs\Common\Decorator\*") added via
"controller/jobs/common/decorators/default" to the job controller.

See also:

* controller/jobs/common/decorators/default
* controller/jobs/product/import/xml/decorators/global
* controller/jobs/product/import/xml/decorators/local

## decorators/global

Adds a list of globally available decorators only to the product import CSV job controller

```
controller/jobs/product/import/xml/decorators/global = Array
(
)
```

* Default: Array
(
)

* Type: array - List of decorator names
* Since: 2019.04

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap global decorators
("\Aimeos\Controller\Jobs\Common\Decorator\*") around the job controller.

```
 controller/jobs/product/import/xml/decorators/global = array( 'decorator1' )
```

This would add the decorator named "decorator1" defined by
"\Aimeos\Controller\Jobs\Common\Decorator\Decorator1" only to the job controller.

See also:

* controller/jobs/common/decorators/default
* controller/jobs/product/import/xml/decorators/excludes
* controller/jobs/product/import/xml/decorators/local

## decorators/local

Adds a list of local decorators only to the product import CSV job controller

```
controller/jobs/product/import/xml/decorators/local = Array
(
)
```

* Default: Array
(
)

* Type: array - List of decorator names
* Since: 2019.04

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap local decorators
("\Aimeos\Controller\Jobs\Product\Import\Xml\Decorator\*") around the job
controller.

```
 controller/jobs/product/import/xml/decorators/local = array( 'decorator2' )
```

This would add the decorator named "decorator2" defined by
"\Aimeos\Controller\Jobs\Product\Import\Xml\Decorator\Decorator2"
only to the job controller.

See also:

* controller/jobs/common/decorators/default
* controller/jobs/product/import/xml/decorators/excludes
* controller/jobs/product/import/xml/decorators/global

## domains

List of item domain names that should be retrieved along with the attribute items

```
controller/jobs/product/import/xml/domains = Array
(
    [attribute] => attribute
    [catalog] => catalog
    [media] => media
    [price] => price
    [product] => product
    [product/property] => product/property
    [supplier] => supplier
    [text] => text
)
```

* Default: Array
(
    [0] => attribute
    [1] => catalog
    [2] => media
    [3] => price
    [4] => product
    [5] => product/property
    [6] => supplier
    [7] => text
)

* Type: array - Associative list of MShop item domain names
* Since: 2019.04

For efficient processing, the items associated to the products can be
fetched to, minimizing the number of database queries required. To be
most effective, the list of item domain names should be used in the
mapping configuration too, so the retrieved items will be used during
the import.

See also:

* controller/jobs/product/import/xml/backup
* controller/jobs/product/import/xml/location
* controller/jobs/product/import/xml/max-query

## location

File or directory where the content is stored which should be imported

```
controller/jobs/product/import/xml/location = /var/www/aimeos/ext/ai-controller-jobs/tests/Controller/Jobs/Xml/Import/_testfiles
```

* Default: product
* Type: string - Relative path to the XML files
* Since: 2019.04

You need to configure the XML file or directory with the XML files that
should be imported. It should be an absolute path to be sure but can be
relative path if you absolutely know from where the job will be executed
from.

See also:

* controller/jobs/product/import/xml/backup
* controller/jobs/product/import/xml/domains
* controller/jobs/product/import/xml/max-query

## max-query

Maximum number of XML nodes processed at once

```
controller/jobs/product/import/xml/max-query = 100
```

* Default: 100
* Type: integer - Number of XML nodes
* Since: 2019.04

Processing and fetching several attribute items at once speeds up importing
the XML files. The more items can be processed at once, the faster the
import. More items also increases the memory usage of the importer and
thus, this parameter should be low enough to avoid reaching the memory
limit of the PHP process.

See also:

* controller/jobs/product/import/xml/domains
* controller/jobs/product/import/xml/location
* controller/jobs/product/import/xml/backup

## name

Class name of the used product suggestions scheduler controller implementation

```
controller/jobs/product/import/xml/name = Standard
```

* Default: Standard
* Type: string - Last part of the class name
* Since: 2019.04

Each default job controller can be replace by an alternative imlementation.
To use this implementation, you have to set the last part of the class
name as configuration value so the controller factory knows which class it
has to instantiate.

For example, if the name of the default class is

```
 \Aimeos\Controller\Jobs\Product\Import\Xml\Standard
```

and you want to replace it with your own version named

```
 \Aimeos\Controller\Jobs\Product\Import\Xml\Myxml
```

then you have to set the this configuration option:

```
 controller/jobs/product/import/xml/name = Myxml
```

The value is the last part of your own class name and it's case sensitive,
so take care that the configuration value is exactly named like the last
part of the class name.

The allowed characters of the class name are A-Z, a-z and 0-9. No other
characters are possible! You should always start the last part of the class
name with an upper case character and continue only with lower case characters
or numbers. Avoid chamel case names like "MyXml"!
