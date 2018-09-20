---
layout: post
title:      "Feeling Validated"
date:       2018-09-20 00:12:12 +0000
permalink:  feeling_validated
---


You might start noticing a trend with me. As I mentioned in my last post, I've been upping my cooking and baking game since moving from San Francisco to a small town full of mediocre chain restaurants. For my Sinatra portfolio project I kept with the cooking theme and decided to create an app that allows users to collect and share recipes.

Honestly, after completing the Sinatra Playlister lab, the rest of the Sinatra projects, including this portfolio project, felt like a walk in the park. I did however explore more with Active Record validations. There's actually a lot that can be done with Active Record validations, so it was fun to look into it more.

My app has two models: Users and Recipes. In both models, I added validations to ensure that a User or Recipe could only be saved if certain conditions have been met.

For the User model, I added the typical validations to ensure the name and email were present and that the email was unique to the User:
```
validates :name, presence: true
validates :email, presence: true
validates :email, uniqueness: true
```

I also added a validation with the help of Regex to ensure the email is in email format:
```
validates :email, format: { with: /\A[^@]+@([^@\.]+\.)+[^@\.]+\z/ }
```

I also set a minimum length requirement for the password by adding this validation:
```
validates :password, length: { minimum: 8 }
```

The bcrypt gem also automatically adds some password validations. With the help of bcrypt, I added a field to the sign up form that asks the user to confirm their password. By default, bcrypt doesn't require the `password_confirmation` attribute to create a User, so I had to add in this validation to make sure users confirm their password when they sign up:
```
validates :password_confirmation, presence: true
```

As for the Recipe model, I added validations for the presence of the recipe name, ingredients, and instructions, but also was able to validate that the serving_size, prep_time, and cook_time were integers, unless left blank. Here's an example of how I did that:
```
validates :serving_size, numericality: { only_integer: true }, allow_nil: true
```

All pretty simple stuff, but I'm excited to dive even deeper into the world of Active Record validations as I move onto the Rails section of the curriculum.
