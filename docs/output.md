Output Handling library bundled with Zest Framework

# Output Handling
Output handling is the way to display the value(which is also called output stream)

## printl function
printl function is use to get language string value form language string file (this function isn't work in components)

```php
  echo printl('home:welcome');
```

## printc function
printc function is use to get language string value form language string file only in components 

```php 
  echo printc('home:welcome');
```

### Note

the language file is locate in Local folder

#### Zest
`App/Local`

#### Components
`App/Components/{name}/Local`
`{name}` refer to component name
