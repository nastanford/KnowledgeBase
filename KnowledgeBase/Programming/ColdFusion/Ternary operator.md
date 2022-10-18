#coldfusion

*ColdFusion v9+*
```php
#((variable eq 'y') ? 'Yes' : 'No')#
```

```php
<!--- Syntax: ((condition) ? trueStatement : falseStatement) --->
<cfset width = ((ThumbnailWidth EQ 0) ? 75 : ThumbnailWidth) />
```

*ColdFusion -v8*
```php
#IIf((variable eq 'y') ,'Yes','No')#
```

```php
<!--- Syntax: IIf(condition, trueStatement, falseStatement) --->
<cfset width = IIf((ThumbnailWidth EQ 0), 75, ThumbnailWidth) />
```