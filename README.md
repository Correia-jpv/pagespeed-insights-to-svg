<p align="center">
	<img src="./assets/banner.svg" >
</p>

<h1 align='center'>PageSpeed Insights scores to SVG</h1>


<h2 align='center'>Generate an SVG of your website's PageSpeed Insights scores</h2>


### Guages
<p align="center">
	<img src="./assets/guages.svg">
</p>

### PWA
<p align="center">
	<img src="./assets/pwa.svg">
</p>

## API and Usage

__Important note: Do not embed url, instead embed generated svg__
- It takes time to perform audits of website. So embedding it directly would not render due to server timeout. Instead you must first visit and download the svg from the API with the desired parameters. And then embed that svg to your files.
- Typically it takes a few seconds to obtain the results from the pagespeed API
- Some servers don't allow (eg. google.com) or delay (eg. cloudflare) pagespeed crawler, so it may result in unexpected results.
- The results may fluctuate slightly sometimes, you can use the ```tests``` parameter to get more accurate perfomance audit results.

### API url
The API is called from `https://pagespeed-insights-svg.glitch.me`

### Simple usage
In simple form it will return result for all categories for desktop version of your website. Replace `your_website_url` with your website's url
```md
https://pagespeed-insights-svg.glitch.me/?url=your_website_url
```
For example
```md
https://pagespeed-insights-svg.glitch.me/?url=https://correiajpv.com
```

### Theme
Default result is theme-agnostic i.e. looks good in both light and dark environment. But you can force one of two additional themes that are `light` and `dark`.
```md
https://pagespeed-insights-svg.glitch.me/?url=your_website_url&theme=dark
```

### Strategy
Strategy specifies the type of device your website is audited for. You can specify strategy as either `mobile` or `desktop`. If none is specified `desktop` is chosen
```md
https://pagespeed-insights-svg.glitch.me/?url=your_website_url&strategy=mobile
```

### Category
There are 5 categories (in order)
- Performance
- Accessibility
- Best Practices
- SEO
- Progressive Web App

By default all the categories are evaluated, but you can specify which categories to evaluate. The category parameter is a number. This is 5-bit number in binary, where if a bit is 1 then the corresponding category will be included.
For example 
```
+------------+------------+------------+------------+------------+
|   Perf.    |    Acc.    |  Best pr.  |     SEO    |     PWA    |
+------------+------------+------------+------------+------------+
|      1     |      0     |      1     |      1     |      1     | => 0x10111 => 23
+------------+------------+------------+------------+------------+
```

#### Only performance
```md
https://pagespeed-insights-svg.glitch.me/?url=your_website_url&categories=16
```

#### All but PWA
```md
https://pagespeed-insights-svg.glitch.me/?url=your_website_url&categories=30
```


### Accuracy

Performance is volatile so you can request up to 3 performance audits to retrieve more precise results
```md
https://pagespeed-insights-svg.glitch.me/?url=your_website_url&tests=3
```

### Embedding into readme
After downloading svg you can embed into readme as following
- markdown
```markdown
![alt text](path/to/svg "tooltip text")
```
- HTML
```html
<p align="center">
    <img src="/path/to/svg" width="XXXpx">
</p>
```

### Keep results updated with action workflow
- [pagespeed.yml](.github/workflows/pagespeed.yml)

### Example
- [Bucket Listy web app README](https://github.com/Correia-jpv/Bucket-listy#development)

### Resources

- [Cloud hosted on Glitch](https://www.glitch.com/)