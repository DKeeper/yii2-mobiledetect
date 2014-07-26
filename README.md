Mobile detector
===============
Detect type of device by information from request.
## Notes

This extension based on mobiledetect project http://mobiledetect.net/.

See [here] (https://github.com/serbanghita/Mobile-Detect/) and [here] (http://demo.mobiledetect.net/) for more documentation and examples.

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist dkeeper/yii2-mobiledetect "*"
```

or add

```
"dkeeper/yii2-mobiledetect": "*"
```

to the require section of your `composer.json` file.


## Usage

Update config file *config/web.php* or *common/main.php*:

```php
return [
    ...
    'components' => [
        'mobiledetect' => [
            'class' => 'dkeeper\mobiledetect\Detect',
        ],
    ],
    ...
];
```

Set event handler for detect type of device before run Application
```php
// path/to/web/index.php
$application = new yii\web\Application($config);

Yii::$app->on(\yii\base\Application::EVENT_BEFORE_REQUEST,function($event){
    Yii::$app->params['detect'] = [
        'isMobile' => Yii::$app->mobiledetect->isMobile(),
        'isTablet' => Yii::$app->mobiledetect->isTablet(),
    ];
});

$application->run();
```