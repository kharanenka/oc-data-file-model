# Trait DataFileModel
 
Trait helps to get attached to the model file data.
For 'attache one' relation returns data array with fields:
  * (string) full_path
  * (string) path
  * (string) title
  * (string) alt

For 'attache many' relation returns array with files data.

#Installation
Require this package in your `composer.json` and update composer.
 
```

"kharanenka/oc-data-file-model": "1.*"

```

#Uses
```php

class MyModel extends Model
{
    use DataFileModel;
    
    public $attachOne = ['preview_image' => 'System\Models\File'];
    public $attachMany = ['images' => 'System\Models\File'];
}

$obModel = MyModel::first();
$arFileData = $obModel->getFileData('preview_image');
$arFileList = $obModel->getFileListData('images');

```
Result:
```php
$arFileData = [
    'full_path' => '...',
    'path'      => '...',
    'title'     => '...',
    'alt'       => '...',
];

$arFileList = [
    [
        'full_path' => '...',
        'path'      => '...',
        'title'     => '...',
        'alt'       => '...',
    ],[
        'full_path' => '...',
        'path'      => '...',
        'title'     => '...',
        'alt'       => '...',
    ],
];
```