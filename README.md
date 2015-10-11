# Mojular templates

A collection of base layout templates for a multiple languages (ERB, Django, Jinja) as well as commong Jinja macros and Rails/Padrino partials.

## Installation

Add as depencency to your project’s `package.json`:

```
npm install https://github.com/mojular/templates/tarball/master --save
```

## Usage

### Django

For version *>=1.8* add the path to your `TEMPLATES` list in the settings file:

```py
TEMPLATES = [
    {
        ...
        'DIRS': [
            root('templates'),
            abspath(root(project_root, 'node_modules', 'mojular-templates')),
        ],
        ...
    },
]
```

For versions *<1.8* add the following:

```py
TEMPLATE_DIRS = (
    root('templates'),
    abspath(root(project_root, 'node_modules', 'mojular-templates'))
)
```

Then extend your templates from Mojular base template.

**Jinja**

```jinja
{% extends 'layouts/jinja/external.html' %}
```

**Django**
```jinja
{% extends 'layouts/django/external.html' %}

```

### ERB

Add the following to `app/controllers/application_controller.rb`

```ruby
layout 'erb/external'

prepend_view_path(File.expand_path("#{Rails.root.to_s}/node_modules/mojular-templates"))
```

`external` is for public use and `internal` is for internal projects.
