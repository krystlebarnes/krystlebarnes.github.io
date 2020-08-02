---
layout: post
title:      "Two Aliases for One User"
date:       2020-08-02 22:02:02 +0000
permalink:  two_aliases_for_one_user
---


For my Rails final project, I've continued to go with the food theme apps and am creating a way to make meal plans from a database of user-submitted recipes. Basically users submit recipes adding to this recipe database. Users can then choose recipes from this database (whether they were the ones to submit it or it was submitted by another user), and add it to their own meal plan. 

At first I wasn't sure how to make one model (the User) essentially have two separate roles (an author of a Recipe and a meal planner) and two separate relations with another model (a Recipe). A user could have many recipes they authored, but a user could also have many recipes they are using for a meal plan. Did I need to split the user into two different models entirely? But would that mean the user would need to have two separate logins depending on if they were authoring a recipe or making a meal plan? That didn't seem to make sense.

The solution was actually much simpler. 

Let's start with the migrations. In my migration for the Recipe table, instead of stating the recipe belongs to a user and adding the user_id as the foreign key, I just said the recipe belongs to an author, and then specified that the author is actually a user. Here's what the code looks like:
```
class CreateRecipes < ActiveRecord::Migration[5.2]
  def change
    create_table :recipes do |t|
      t.string :name
      t.integer :prep_time
      t.integer :cook_time
      t.integer :serving_size
      t.belongs_to :author, references: :users, foreign_key: { to_table: :users}

      t.timestamps
    end
  end
end
```

It's that `t.belongs_to :author, references: :users, foreign_key: { to_table: :users}` that is letting us do some pretty cool things. It's basically saying the recipe belongs to an author so create an author_id column, but it's really a user, so reference the user table and user_id.

I basically then did the same thing for the association between Users as Planners and Recipes. Planners and Recipes is a many-to-many relationship that is joined through the Planned Meals table. This is the code for the migration for the Planned Meals table:

```
class CreatePlannedMeals < ActiveRecord::Migration[5.2]
  def change
    create_table :planned_meals do |t|
      t.date :date
      t.string :meal_type
      t.belongs_to :recipe, foreign_key: true
      t.belongs_to :planner, references: :users, foreign_key: { to_table: :users}

      t.timestamps
    end
  end
end
```

Now, moving onto the models. When defining the associations, you need to identify the foreign_key for associations that involve the User model.

For the Recipe model, it looks like this:
```
has_many :planned_meals
has_many :planners, through: :planned_meals, :class_name => "User", :foreign_key => "planner_id"
belongs_to :author, :class_name => "User", :foreign_key => "author_id"
```

For the Planned Meal model, I added these lines:
```
belongs_to :recipe
belongs_to :planner, :class_name => "User", :foreign_key => "planner_id"
```

Lastly, for the User model, I added this:
```
has_many :planned_meals, :foreign_key => "planner_id"
has_many :recipes, through: :planned_meals, :foreign_key => "planner_id"
has_many :recipes, :foreign_key => "author_id"
```

Now everything should be connected and the User has the ability to author a Recipe and use a Recipe in their meal plan without having to use a separate login. Crisis averted.



