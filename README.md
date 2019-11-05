# Track page view in Vue.js app while using both Google Analytic and Google AdWord

In case you want to use Google Adword and Google Analytic together on your Vue.js app, and you want to show Pageviews prperly on your Google Analytic, you should follow these steps. You should link your Google AdWord account to your Google Analytic beside these steps. This instruction is only focused on coding section.

1. Add Global site tag script right after head tag in you main html file. (For example index.html)
  
  ```
  <head>
    <!-- Global site tag (gtag.js) - Google Ads: XXXXXXXX -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=AW-XXXXXXXX"></script>
  <!-- rest of tags in header -->
  </head>
  ```
  
  2. Add Config section before closing head tag

```
  <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());

      // this is from Google Analytic tracking code
      gtag('config', 'UA-XXXXXXXX-X');
      
      //this is from Google AdWord code
      gtag('config', 'AW-XXXXXXXX');
 </script>
```

3. Now inside each page of your vue app, you can choose a component, and inside its mounted() method, inject pageview tracking code.

```
//mounted() of component A in page 1
mounted(){
            gtag('config', 'UA-XXXXXXXX-X', {
                'page_title' : 'Page title 1',
                'page_path': '/'
            })
},
```

and in another page


```
//mounted() of component B in page 2
mounted(){
            gtag('config', 'UA-XXXXXXXX-X', {
                'page_title' : 'Page title 2',
                'page_path': '/page-2'
            })
},
```

// TODO: Add gtag_report_conversion methods
