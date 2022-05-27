# Migrations

## Create a new model

```ruby
  class CreateMyModel < ActiveRecord::Migration[6.1]
    def change
      create_table :my_table do |t|
        t.string :name
      end
    end
  end
```

## Rollback multiple steps
Can be achieved using the `STEP` variable:

```shell
rails db:rollback STEP=2
```
will roll back the last two migrations
