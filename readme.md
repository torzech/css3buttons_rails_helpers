# css3buttons gem - helper methods for css3buttons

The css3buttons gem is a small set of helper methods designed to work in
conjunction with the __amazing__ [css3 github buttons by Nicolas Gallagher](http://nicolasgallagher.com/lab/css3-github-buttons/).

The helpers allow rails developers to quickly and easily leverage this
fantastic CSS library - without cluttering up your views and calls to
`link_to`, `button_to` and `submit_tag`.

# What's new in version this version?

In this version we've updated the css to now work with the [css3 github buttons](http://nicolasgallagher.com/lab/css3-github-buttons/) as standard, instead of the original css3buttons, to take advantage of a few of the features not included in the original library.

Additionally, there was some serious re-tooling of the helper methods to make them more usable, more dynamic and less prone to error.

__Please note__: as part of changes, calls to `link_button_to` will need
to be updated to `button_link_to`. Everything else should work expected.


# Getting started

Include the gem in your gemfile:

    gem 'css3buttons'

Run the generators

    $ rails g css3buttons

Which will copy the stylesheets and icon/button images into your public
directory.

In your layout, add the following:

    <%= css3buttons_stylesheets %>

Which will add both the `reset.css` and the `css3buttons.css` stylesheet
link tags. 

_Please note_ since this helper includes the css3buttons
reset stylesheet, it's advisable to place this helper before all your
other stylsheet declarations. However, if you'd like to use your own
reset, you can skip it with:

    <%= css3buttons_stylesheets :include_reset => false %>


# The basics

To change your `link_to` calls to buttons, simply use `button_link_to`.
For example:

    <%= button_link_to "Search", search_path %>

The helper method accept all the same parameters as `link_to` so
upgrading and downgrading so css3buttons should be a snap.


# Icons and pills and colours, oh my!

The gem also responds to a huge list of dynamic helper methods, to assist in adding
icons, colours and styles to your buttons. Unlike previous versions of
the gem, you can now add any of the features in any order.


## Icons

To add an icon from [the current icon list](http://nicolasgallagher.com/lab/css3-github-buttons/), simply prepend the helper method with the name of the icon you'd like to use. For example:

    <%= magnifier_button_link_to "Search", search_path %>
    <%= user_button_link_to "Account", edit_current_user_path %>
    <%= pin_button_link_to "Mark on map", edit_map_path %>


## Styles

Just like the icons, you can add options for `primary`, `big` and
`pill`.

    <%= primary_button_link_to "Home", root_path %>
    <%= pill_button_link_to "Archive", archive_path %>
    <%= big_primary_pill_button_link_to "Super Important!", super_important_path %>


## Colors

Again with colors - simply add `positive` or `negative` to the front of your method call:

    <%= negative_trash_button_to "Delete", delete_path %>
    <%= positive_pill_reload_button_to "Reload", reload_path %>

In order to be compatible with the new css3 github buttons library, you are also able to use `safe` and `danger` - as an alternative.


## Button groups

Button groups are snap, you just need to wrap your buttons with `button_group`, like so:

    <%= button_group do %>
      <%= link_button_to "Show", @post %>
      <%= link_button_to "Edit", edit_post_path(@post) %>
      <%= negative_trash_button_to "Delete", @post, :confirm => "Are you sure? %>
    <% end %>

And, of course, minor groups:

    <%= minor_button_group => true do %>
      You know the drill by now.
    <% end %>

## Other stuff

Submit tags are also ushered in with this version. Everything works as it does above, except instead of `button_link_to` it's `button_submit_tag`. Example:

    <%= positive_button_submit_tag "Publish" %>


# What's missing?

The `button_group` helper needs some proper tests, if anyone can point me
as to how to stub out a rails request template in RSpec, that would be much
appreciated!

I've noticed that this version of the css3 github buttons does not include any colours for the positive/safe styles - so this will appear as normal buttons, unless you add your own styling.

Forks and pull requests are always welcome.
