# techsmart-web-app
1. Create the basic structure of laravel and add the make:auth to the website 
2. Add the Admin lte to the website using the below command:
```
npm install admin-lte@v3.0.0-alpha.2 --save
```
3. Create a new __master.blade.php__ file in the layouts folder, remove the css and js links and new links:

```
 <link rel="stylesheet" href="/css/app.css">
 <script src="/js/app.js"></script>

```
4. Change the __extends('layouts.app')__ to __extends('layouts.master')__ in __home.blade.php

5. 
