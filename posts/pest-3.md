---
Image:
Title: What's new in Pest 3 and how to upgrade
Description: Explore the exciting new features in Pest 3, including architecture test presets and simplified upgrading. Learn how to step up your PHP testing game with this awesome update!
Canonical: 
Audio:
Published at: 2024-08-27
Modified at:
Categories: php
---

## Introduction

[Pest](https://pestphp.com), my favorite PHP testing framework, has just dropped its version 3, and I couldn't wait to dive in and share my thoughts with you.

## The easiest upgrade ever?

Before we get into the juicy new features, let's talk about upgrading. Spoiler alert: it's ridiculously simple. All you need to do is bump up your dependency to `^3.x-dev` in your `composer.json` file. That's it! No breaking changes to worry about, no tedious refactoring – just a smooth sail to the latest and greatest version of Pest.

```json
{
    "require-dev": {
        "pestphp/pest": "^3.x-dev"
    }
}
```

Run `composer update`, and you're good to go. Now, let's dive into what's new!

## What's new in Pest 3?

### Architecture tests presets: A game-changer for structural integrity

One of the standout features in Pest 3 is the introduction of architecture tests presets. This is a powerful tool that allows us to enforce architectural rules and best practices in our codebase.

Pest 3 comes with several presets out of the box:

- Laravel
- PHP
- Relaxed
- Security
- Strict

Using these presets is as simple as calling a method. For example, if you're working on a Laravel project, you can use the Laravel preset like this:

```php
arch()->preset()->laravel();
```

This will apply a set of architectural rules that are tailored for Laravel applications, helping you maintain a clean and consistent codebase.

But what if you need to make exceptions? Pest 3 has got you covered. You can exclude specific files or namespaces using the `ignoring()` method. For instance:

```php
arch()->preset()->laravel()->excluding('App\Models\Scopes');
```

This flexibility allows you to adhere to best practices while still accommodating the unique needs of your project.

### Mutation testing: The future of test reliability

Pest 3 is also introducing mutation testing, which is an exciting development in the world of software testing. While I don't have all the details yet, mutation testing is a technique that involves making small changes (mutations) to your code and running your tests against these mutated versions. This helps identify weak spots in your test suite and ensures your tests are truly effective.

I'm really looking forward to exploring this feature more and seeing how it can improve the reliability of our test suites. Stay tuned for more information on this!

### Todos management with GitHub: Streamlining your workflow

Another intriguing feature coming with Pest 3 is todos management integrated with GitHub. While the specifics aren't clear yet, this sounds like it could be a great way to keep track of tasks and improvements directly from your test suite. Imagine being able to flag areas that need attention and have them automatically sync with your GitHub issues – that's the kind of seamless workflow I'm always excited about.

I'll be sure to update you all once I have more information on how this feature works and how we can leverage it in our projects.