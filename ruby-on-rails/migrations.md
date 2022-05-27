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
