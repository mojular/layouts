# Mojular templates

A collection of base layout templates for multiple template languages (ERB, Django, Jinja). Also common Jinja macros and Rails/Padrino partials.

## Installation

Add as depencency to your project’s `package.json`:

```
npm install mojular/templates --save
```

## Usage

See [examples](https://github.com/mojular/examples) of using templates with different frameworks.

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
layout 'erb/base'

prepend_view_path(File.expand_path("#{Rails.root.to_s}/node_modules/mojular-templates"))
```

`external` is for public use and `internal` is for internal projects.
