## Sitemap generator

---

Object based PHP script that generates a XML sitemap with the given config options. 

Modified from Tristan Goossens
https://github.com/tristangoossens/php-sitemap-generator

Sitemap format: [http://www.sitemaps.org/protocol.html](http://www.sitemaps.org/protocol.html)

### Features

- [x] Generate a sitemap for your website
- [x] Multiple options for generating sitemaps
- [x] Option to ignore filetypes (like .jpg or .png)
- [x] Option to drop slashes from the end of the URL

### Installation

Installing this script is simply just downloading both `sitemap_config` and `sitemap_generator` and placing them into your project(same directory).

### Usage

After installing the script you can use the script by including it into your script

```php
include "sitemap-generator.php";
```

And initializing the class by calling the constructor

```php
// Create an object of the generator class passing the config file
$smg = new SitemapGenerator(include("sitemap-config.php"));
// Run the generator
$smg->GenerateSitemap();
```

Alternatively, pass your array of settings directly

```php
$url = "https://whateveryoudecide.com";

// Set up your Variables
$conf = array(
    "SITE_URL" => $url,
    "ALLOW_EXTERNAL_LINKS" => false,
    "ALLOW_ELEMENT_LINKS" => false,
    "CRAWL_ANCHORS_WITH_ID" => "",
    "KEYWORDS_TO_SKIP" => array(),
    "SAVE_LOC" => "sitemap.xml",
    "PRIORITY" => 1,
    "CHANGE_FREQUENCY" => "daily",
    "LAST_UPDATED" => date('Y-m-d'),
    "SKIP_EXTENSIONS" => array("jpg", "png"),
    "REMOVE_LAST_SLASH" => true
);

// Create an object of the generator class passing the config file
$smg = new SitemapGenerator($conf);

// Run the generator
$smg->GenerateSitemap();
```

### Config

You can alter some of the configs settings by changing the config values.

```php

"SITE_URL" => "https://student-laptop.nl/",

"ALLOW_EXTERNAL_LINKS" => false,

"ALLOW_ELEMENT_LINKS" => false,

"CRAWL_ANCHORS_WITH_ID" => "",

"KEYWORDS_TO_SKIP" => array(
    "http://localhost/student-laptop/index", // I already have a href for root ("/") on my page so skip this page
    "/student-laptop/student-laptop.nl/", // Invalid link example
),

"SAVE_LOC" => "sitemap.xml",

"PRIORITY" => 1,

"CHANGE_FREQUENCY" => "daily",

"LAST_UPDATED" => date('Y-m-d'),

"SKIP_EXTENSIONS" => array("jpg", "png"),
    
"REMOVE_LAST_SLASH" => true
```

### Output

Example output when generating a sitemap using this script

```XML
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <!-- 3 total links-->
  <!-- PHP-sitemap-generator by https://github.com/tristangoossens -->
  <url>
    <loc>https://student-laptop.nl/</loc>
    <lastmod>2021-03-10</lastmod>
    <changefreq>daily</changefreq>
    <priority>1</priority>
  </url>
  <url>
    <loc>https://student-laptop.nl/underConstruction</loc>
    <lastmod>2021-03-10</lastmod>
    <changefreq>daily</changefreq>
    <priority>1</priority>
  </url>
  <url>
    <loc>https://student-laptop.nl/article?article_id=1</loc>
    <lastmod>2021-03-10</lastmod>
    <changefreq>daily</changefreq>
    <priority>1</priority>
  </url>
</urlset>
```
