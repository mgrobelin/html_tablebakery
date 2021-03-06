html_tablebakery
================

Generate HTML tables for Ruby/RoR

= Usage

* include table bakery as git submodule
```
rails new cool_rails_app
cd cool_rails_app
git submodule add git@github.com:mgrobelin/html_tablebakery.git lib/html_tablebakery
```

* add to applications load path

```
# application.rb
module CoolRailsApp
  class Application < Rails::Application
    config.eager_load_paths += %W(
      #{config.root}/lib/html_tablebakery
    )
  end
end
```

* configure presets

```
# config/initializers/tablebakery_presets.rb
# default presets for HtmlTablebakery
TABLEBAKERY_PRESETS = {
    system: {
        attr_ignore: %w( id created_at updated_at operating_system_flavour ),
        attr_order:  %w( name fqdn operating_system join actions )

    },
    service: {
        attr_ignore: %w( id updated_at created_at ),
        attr_order:  %w( name type actions)
    },
    test_plan: {
        attr_ignore: %w( id updated_at created_at user_id ),
        attr_order:  %w( name description base_url actions)
    },
    test_item: {
        attr_ignore: %w( id updated_at created_at ),
        attr_order:  %w( name description type format markup actions)
    },
    test_case: {
        attr_ignore: %w( updated_at created_at type ),
        attr_order:  %w( id name description format markup actions)
    },
    test_script: {
        attr_ignore: %w( updated_at created_at type ),
        attr_order:  %w( id name description format markup actions)
    },
    test_execution: {
        attr_ignore: %w( id updated_at user_id ),
        attr_order:  %w( created_at job_id name test_plan_id base_url actions)
    }
}
```

  * include as application helper
```
# app/helpers/application_helper.rb
module ApplicationHelper
    include HtmlTablebakery
end
```
