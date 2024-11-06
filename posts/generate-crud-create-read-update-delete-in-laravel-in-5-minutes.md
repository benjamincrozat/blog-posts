---
Image: https://i.postimg.cc/sfPNdzvr/image.png
Title: Generate a Laravel CRUD (Create, Read, Update, Delete) in 5 minutes.
Description: Generate CRUDs in Laravel using Backpack.
Canonical: https://backpackforlaravel.com/articles/getting-started/generate-crud-create-read-update-delete-in-laravel-in-5-minutes
Audio:
Published at: 2024-04-21
Modified at:
Categories: laravel, packages
---

Are you building your App on Laravel? That's a great choice🎉. You must be planning an **Admin panel** for it. Well, if you're building one, let me give an overview of how you can make a customizable & functional Admin panel with **less effort**.

Admin Panels are made of [CRUDs](https://backpackforlaravel.com/docs/6.x/getting-started-basics#whats-a-crud), [Charts](https://backpackforlaravel.com/docs/6.x/base-widgets#chart-pro), and [Widgets](https://backpackforlaravel.com/docs/6.x/base-widgets). The major component is the CRUD, which is built with various fields and columns. I'm writing this article about a package that will help you generate **Laravel CRUDs** in just 5 minutes.

![image](https://i.postimg.cc/sfPNdzvr/image.png)

# Installation.

We'll be using [https://backpackforlaravel.com](https://backpackforlaravel.com) to generate Laravel CRUDs. You can experience a Monster CRUD in the [live demo](https://demo.backpackforlaravel.com/admin/monster) and be more confident in giving it a shot. So, are you ready?

Let's install it now:

1. Go to your Laravel project's directory, then in your terminal, run:


```shell
composer require backpack/crud
```

2. Follow the prompts - in the end, the installer will also tell you your admin panel's URL, where you should go and login.


```shell
php artisan backpack:install
```

> Note: Make sure the `APP_URL` in your .env file is correctly pointing to the URL you use to access your application in the browser, for example: `http:127.0.0.1:8000` or [`http://something.test`](http://something.test)

If you are facing trouble, check the [installation](https://backpackforlaravel.com/docs/6.x/installation) page for help!

## Laravel CRUD with a single command

To generate Laravel CRUD, we need a table.

1. Let's assume we have the `tags` table. You can copy the following migration to make one.


```php
Schema::create('tags', function (Blueprint $table) {
  $table->increments('id');
  $table->string('name');
  $table->string('slug')->unique();
  $table->timestamps();
});
```

2. Now, We'll run the following command to generate CRUD:


```bash
php artisan backpack:crud tag # use singular, not plural (like the Model name)
```

The code above will generate the following:

* a model (`app/Models/Tag.php`);
* a controller (`app/Http/Controllers/Admin/TagCrudController.php`);
* a request (`app/Http/Requests/TagCrudRequest.php`);
* a resource route, as a line inside `routes/backpack/custom.php`;
* a new menu item in `resources/views/vendor/backpack/ui/inc/menu_items.blade.php`;

Done! Go to https://localhost/admin/tag to see your Laravel CRUD in action.

## CRUD Customization

We'll go through the generated files and customize them per project needs. Majorly customization includes:

* **Field** types for Create & Update Form.
* **Columns** types for List & Show.


Let's look at the generated Controller `TagCrudController.php` and add Fields & Columns:

```diff
<?php
...
use Backpack\CRUD\app\Library\CrudPanel\CrudPanelFacade as CRUD;

class TagCrudController extends CrudController
{
    ...
    protected function setupListOperation()
    {
+       CRUD::column('name')->type(text);
+       CRUD::column('slug')->type(text);
    }

    protected function setupCreateOperation()
    {
        CRUD::setValidation(TagRequest::class);
+       CRUD::field('name')->type(text);
+       CRUD::field('slug')->type(text);
    }
    ...
}
```

This less gets you a fully working CRUD:

![image](https://i.postimg.cc/kXXw8DcS/chrome-capture-2024-3-17-1.gif)

### Available Fields & Columns

Backpack includes a variety of FREE [Fields](https://backpackforlaravel.com/docs/6.x/crud-fields) & [Columns](https://backpackforlaravel.com/docs/6.x/crud-columns) and some eye-catching PRO Fields(single addon) for complex project needs:

| FREE Fields |  | PRO Fields |  |
| --- | --- | --- | --- |
| checkbox | checklist | address\_google | browse |
| checklist\_dependency | color | browse\_multiple | base64\_image |
| custom\_html | date | ckeditor | date\_range |
| datetime | email | date\_picker | datetime\_picker |
| enum | Database ENUM | dropzone | easymde |
| PHP enum | hidden | google\_map | icon\_picker |
| month | number | image | phone |
| password | radio | relationship | repeatable |
| select (1-n) | select\_grouped | select2 (1-n) | select2\_multiple (n-n) |
| select\_multiple (n-n) | select\_from\_array | select2\_nested | select2\_grouped |
| summernote | switch | select\_and\_order | select2\_from\_array |
| text | textarea | select2\_from\_ajax | select2\_from\_ajax\_multiple |
| time | upload | slug | table |
| upload\_multiple | url | tinymce | video |
| view | week | wysiwyg |  |

You are also free to make one if not counted above. It's just a [command](https://backpackforlaravel.com/docs/6.x/crud-fields#creating-a-custom-field-type-1) away.

## CRUD Addons

Backpack also has many CRUDs and addons ready to use, which you can find [here](https://backpackforlaravel.com/addons). It includes **SettingsCRUD**, **MenuCRUD**, **NewsCRUD**, **User, Role & Permissions CRUD**, and many other useful admin panel features.

If you are wondering🤔 how to inject JS to backpack fields to show/hide on the client side, check out [CrudField JavaScript Library](https://backpackforlaravel.com/docs/6.x/crud-fields-javascript-api). Backpack is a robust package that stops you nowhere.

## Conclusion

[Laravel](https://laravel.com/) is excellent at building #PHP applications, and [Backpack](https://backpackforlaravel.com/) is excellent at building Laravel CRUDs & Admin Panel. Check out the wide variety of [fields & columns](https://backpackforlaravel.com/docs/6.x/crud-fields) it offers.

Give it a try, and experience generating Laravel CRUDs in 5 minutes. You'll never go back -- because we're all lazy😝. For more info, visit Backpack's FREE [CRUD Crash Course](https://backpackforlaravel.com/docs/6.x/crud-tutorial).