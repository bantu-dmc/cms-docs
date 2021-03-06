#  Google Analytics

- [How to obtain the credentials to communicate with Google Analytics](#how_to)
    - [Getting credentials](#getting_credentials)
    - [Granting permissions to your Analytics property](#granting_permissions)
    - [Getting the view id](#getting_view_id)
- [Usage](#usage)
- [Provided methods](#provided_methods)
    - [Visitors and page views](#visitor_and_page_views)
    - [Most visited pages](#most_visit_pages)
    - [Top referrers](#top_referrers)
    - [Top browsers](#top_browsers)
    - [All other Google Analytics queries](#other_queries)

Reference: https://github.com/spatie/laravel-analytics

> Because spatie/laravel-analytics package is just support PHP 7, so I need to customize it to support PHP 5.6 again.

Here are a few examples of the provided methods:

```php
use Botble\Analytics\Period;

//fetch the most visited pages for today and the past week
Analytics::fetchMostVisitedPages(Period::days(7));

//fetch visitors and page views for the past week
Analytics::fetchVisitorsAndPageViews(Period::days(7));
```

Most methods will return an `\Illuminate\Support\Collection` object containing the results.

The config file stored in `config/laravel-analytics.php`

```php

return [
    /*
     * The view id of which you want to display data.
     */
    'view_id' => env('ANALYTICS_VIEW_ID'),

    /*
     * Path to the json file with service account credentials. Take a look at the README of this package
     * to learn how to get this file.
     */
    'service_account_credentials_json' => storage_path('app/laravel-google-analytics/service-account-credentials.json'),

    /*
     * The amount of minutes the Google API responses will be cached.
     * If you set this to zero, the responses won't be cached at all.
     */
    'cache_lifetime_in_minutes' => 60 * 24,
];

```

<a name="how_to"></a>
## How to obtain the credentials to communicate with Google Analytics

<a name="getting_credentials"></a>
### Getting credentials

The first thing you’ll need to do is to get some credentials to use Google API’s. I’m assuming that you’ve already created a Google account and are signed in. Head over to [Google API’s site](https://console.developers.google.com/apis) and click "Select a project" in the header.

![1](https://spatie.github.io/laravel-analytics/v2/1.jpg)

Next up we must specify which API’s the project may consume. In the list of available API’s click "Google Analytics API". On the next screen click "Enable".

![2](https://spatie.github.io/laravel-analytics/v2/2.jpg)

Now that you’ve created a project that has access to the Analytics API it’s time to download a file with these credentials. Click "Credentials" in the sidebar. You’ll want to create a "Service account key".

![3](https://spatie.github.io/laravel-analytics/v2/3.jpg)

On the next screen you can give the service account a name. You can name it anything you’d like. In the service account id you’ll see an email address. We’ll use this email address later on in this guide. Select "JSON" as the key type and click "Create" to download the JSON file.

![4](https://spatie.github.io/laravel-analytics/v2/4.jpg)

Save the json inside your Laravel project at the location specified in the `service_account_credentials_json` key of the config file of this package. Because the json file contains potentially sensitive information I don't recommend committing it to your git repository.

<a name="granting_permissions"></a>
### Granting permissions to your Analytics property

I'm assuming that you've already created a Analytics account on the [Analytics site](https://analytics.google.com/analytics). Go to "User management" in the Admin-section of the property.

![5](https://spatie.github.io/laravel-analytics/v2/5.jpg)

On this screen you can grant access to the email address found in the `client_email` key from the json file you download in the previous step. Read only access is enough.

![6](https://spatie.github.io/laravel-analytics/v2/6.jpg)

<a name="getting_view_id"></a>
### Getting the view id

The last thing you'll have to do is fill in the `view_id` in the config file. You can get the right value on the [Analytics site](https://analytics.google.com/analytics). Go to "View setting" in the Admin-section of the property.

![7](https://spatie.github.io/laravel-analytics/v2/7.jpg)

You'll need the `View ID` displayed there.

![8](https://spatie.github.io/laravel-analytics/v2/8.jpg)

<a name="usage"></a>
## Usage

When the installation is done you can easily retrieve Analytics data. Nearly all methods will return an `Illuminate\Support\Collection`-instance.


Here is an example to retrieve visitors and pageview data for the current day and the last seven days.
```php
$analyticsData = Analytics::fetchVisitorsAndPageViews(Period::days(7));
```

`$analyticsData` is a `Collection` in which each item is an array that holds keys `date`, `visitors` and `pageViews`

If you want to have more control over the period you want to fetch data for, you can pass a `startDate` and an `endDate` to the period object.

```php
$startDate = Carbon::now();
$endDate = Carbon::now()->subYear();

Period::create($startDate, $endDate);
```

<a name="provided_methods"></a>
## Provided methods

<a name="visitor_and_page_views"></a>
### Visitors and page views

```php
public function fetchVisitorsAndPageViews(Period $period): Collection
```

The function returns a `Collection` in which each item is an array that holds keys `date`, `visitors`, `pageTitle` and `pageViews`.

<a name="most_visit_pages"></a>
### Most visited pages

```php
public function fetchMostVisitedPages(Period $period, int $maxResults = 20): Collection
```

The function returns a `Collection` in which each item is an array that holds keys `url`, `pageTitle` and `pageViews`.

<a name="top_referrers"></a>
### Top referrers

```php
public function fetchTopReferrers(Period $period, int $maxResults = 20): Collection
```

The function returns a `Collection` in which each item is an array that holds keys `url` and `pageViews`.

<a name="top_browsers"</a>
### Top browsers

```php
public function fetchTopBrowsers(Period $period, int $maxResults = 10): Collection
```

The function returns a `Collection` in which each item is an array that holds keys `browser` and `sessions`.

<a name="other_queries"></a>
### All other Google Analytics queries

To perform all other queries on the Google Analytics resource use `performQuery`.  [Google's Core Reporting API](https://developers.google.com/analytics/devguides/reporting/core/v3/common-queries) provides more information on on which metrics and dimensions might be used.

```php
public function performQuery(Period $period, string $metrics, array $others = [])
```

You can get access to the underlying `Google_Service_Analytics` object:

```php
Analytics::getAnalyticsService();
```