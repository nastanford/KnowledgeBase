#coldfusion

*ColdFusion v9+*
```php
#((variable eq 'y') ? 'Yes' : 'No')#
```

##### Syntax: ((condition) ? trueStatement : falseStatement)
```php
<cfset width = ((ThumbnailWidth EQ 0) ? 75 : ThumbnailWidth) />
```

*ColdFusion -v8*
```php
#IIf((variable eq 'y') ,'Yes','No')#
```

#### Syntax: IIf(condition, trueStatement, falseStatement)
```php
<cfset width = IIf((ThumbnailWidth EQ 0), 75, ThumbnailWidth) />
```

