# jQuery.has-many.js

This plugin helps you to create variadic relations on a CRUD page without
having to save the new object before you can add relations.

It handles both new objects and existing objects.

## Wat?

Let's say you have a CRUD page for an e-marketing system that sets up discounts.
The CRUD page itself would display an HTML form for the single discount model in question, such
as the product to which it applies and the discount to add.

Then on a separate tab you have a table containing a form, where you can add the business logic
that determines the applicability of a discount.

This poses various problems with keeping track of what's new, what's edited, what's deleted, possibly
attaching AJAX to the rows, keeping a new row available, that sort of thing.

This plugin therefore tries to intelligently keep a handle on all of that for you:

* Handles the save, remove and add buttons
* Ensures a new row is always available
* Knows whether a row was already there, or whether it was created by the plugin
* Ensures all fields have unique names

## Usage

    $('.has-many-table').hasMany();

That's easy isn't it?

Well this assumes various defaults, which can be overridden by providing an options object with any of the following properties:

* owner_id - This is the ID of the model whose CRUD page this is, and by default comes from `data-has-many` on the table.
* owner_field_name - The field name by which the CRUD page is naming this relation.
* new_row - The blank row that adds a new one, defaulting to the last tr in the table.
* add_button - The button to click to add the input row to the list. Defaults to an element in the new_row with both classes `btn` and `add`.
* remove_button - The button to click to remove a row. This is expected to exist in new_row because new_row will be cloned and the add button replaced with the remove button. Searches for an element with `btn` and `remove` classes.
* field_names - This is an array of the field names in each row. It defaults to finding all inputs in new_row that look like `owner_field_name[(id)?][field_name]`.
* validation - You can provide a function that accepts a row and returns true or false. By default there is no validation run.

## Bugs and TODOs

* The remove_button option is not used to find existing remove buttons
