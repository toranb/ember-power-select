# Master

- [BUGFIX] The overflow-y should be auto to not show the bar until it's required by the height of the
  option list.

# 0.6.0-beta.3
- [BUGFIX] Remove loading state if a promise fullfils after the dropdown has been closed

# 0.6.0-beta.2
- [BUGFIX] Update to ember-cli 1.13.13 to remove `[DEPRECATED] this.Funnel ...`  message.
- [BUGFIX] Fix styles when rendering the component in place
- [BUGFIX] Fix position calculation in firefox.
- [BUGFIX] Using `dropdownPosition=above|below` adds the proper class names to the component.
- [DOCS] Fixed typos and outdated links.

# 0.6.0-beta.1
- [BUGFIX] Add missing `this._super.included(app);` in the included hook so runtime dependencies are
  required.

# 0.6.0-beta.0
- [BREAKING CHANGE] The arguments received by the `selectComponent` and `optionsComponent` have changed
  significantly as a result of an internal refactor. It should not affect to people that have not created
  their own customized versions of ember-power-select.
- [BUGFIX] Ensure that open the dropdown after a search does not clear the results. Results are not
  cleared when the component is closed, like the `searchText`.
- [BUGFIX] Ensure `options` and `search` play nicely toguether. The given options are the initial set of
  results until the user performs the first search. From that point on they diverge.
- [BUGFIX] Not return from the `search` action is now legal. If you do so, you need to take care
  of updating the `options` yourself, and unless you make options a promise, you will loose the
  loading state.

# 0.5.2
- [BUGFIX] Don't render one option for the Loading message if this is falsey

# 0.5.1
- [BUGFIX] Fix automatic scroll when navigating using arrows.

# 0.5.0
- [BREAKING CHANGE] Some classes have changed to be more BEMy and avoid class collisions. You can expect
  things like `.nested`, `.selected`, `.highlighted`, etc.. to be not copies of the default class of that
  element but with `--nested`, `--selected`, etc... modifiers.
- [BREAKING CHANGE] The arrow of the dropdown is not longer a background image, but an `<span class="ember-power-select-status-icon">`,
  that you can style in more complex ways. By default is still a triangle (but done with css borders instead)
- [BUGFIX] Fixed `rtl`/`ltr` styles.

# 0.4.4
- [ENHANCEMENT] Allow to customize tabindex of the trigger
- [ENHANCEMENT] Pass `select` action and `highlighted` option to the selectedComponent to allow better
  customization

# 0.4.3
- [ENHANCEMENT] Pass `search` action to the selected component also for single component.
  This enables ember-power-select to to be the base for typeahead-like components.
- [BUGFIX] Fix placeholder of multiple select showing "null".

# 0.4.2
- [BUGFIX] Stop propagation of the events that trigger the `select` action. This was preventing
  to use this component within another component that closes when clicking on the body, like
  the ember-basic-dropdown

# 0.4.1
- [BUGFIX] Get subpixed precission on Y coordinates too by updating to ember-basic-dropdown 0.4.7

# 0.4.0
- [BREAKING] Remove {{ember-power-select}} deprecated alias for {{power-select}}
- [BREAKING] Remove `ember-power-select-wrapper` wrapped div that was not customizable and made styling harder.
             Now the topmost element is the `ember-power-select` itself.
- [BUGFIX] Update ember-basic-dropdown to fix rounding error that caused list of options have 1px mismatch in HD screens
- [TOOLING] Update to ember-cli 1.13.10

# 0.3.9
- [BUGFIX] Apply `dropdownClass` to the dropdown

# 0.3.8
- [BUGFIX] Disable the input of multiple selects when the entire component is disabled
- [BUGFIX] Don't show the cross to remove items when the entire component is disabled
- [ACCESIBILITY] Add aria-label to cross to remove items in multiple mode

# 0.3.7
- [BUGFIX] Open multiple select when the user types on the input of the trigger

# 0.3.6
- [REFACTOR] Variables in it's own file for encapsulations and allow more fine-grained customizations

# 0.3.5
- [BUGFIX] Update ember-basic-dropdown to fix deprecation warning coming from accessing `_actions`.
- [INTERNAL] For consistency, since the component's name was shortened to {{power-select}}, all internal
  components have been renamed too. No public API changes.

# 0.3.4
- [BUGFIX] Fix placeholder bug in multiple selects (show "null" as placeholder)
- [BUGFIX] Fix unused scss variable ($ember-power-select-text-color) and make it `inherit` by default instead of `#444`.
- [DOCS] Clarify that in "How to use" section selects are broken intentionally to explain why explicitness is good.

# 0.3.3
- [DEPRECATION] Renamed component from {{ember-power-select}} to just {{power-select}} and deprecate the long name.
- [BUGFIX] Increate z-index to 1000 (same that bootstrap uses for dropdowns)
- [BUGFIX] Add support for placeholder in multiple mode
- ... some internal refactors to make the selected item easier to customize

# 0.3.2
- [BUGFIX] Pressing enter on a closed multiple select should open it.
- [ENHANCEMENT] Pressing UP/DOWN arrows on a closed select (single or multiple) opens it

# 0.3.1
- [ENHANCEMENT] Added `closeOnSelect` option (defaults to true) to customize that behavior.
- [ENHANCEMENT] The `onchange` action is not invoked with the `dropdown` as second argument. That
  object contains methods like `open`, `close` and `toggle` that give control over the
  dropdown to the user.
- [BUGFIX] Select that specify a `search` action can also receive `options` now, and that collection
  is displayed until the user performs the first search.
- [BUGFIX] The `search` action now is also triggered when the search term is an empty string.

# 0.3.0
- [BREAKING CHANGE] The component is truly immutable now. The value inside the trigger (the selected value) won't update unless
  the user explicitly does so inside the `onchange` action. Since selection never were propagated upstream this shouldn't
  bite anyone: A select component without an action handles was pointless anyway. Now there is an assertion that will raise
  an error if no `onchange` action is provided (or it's not a function).
- [ENHANCEMENT] The component used to render the list is not replaceable. That allows almost complete customization.


# 0.2.6
- [BUGFIX] Workaround bug in ember <= 1.13.8
- [ENHANCEMENT] Added basic bootstrap styles.

# 0.2.1
- [REFACTOR] Divide component internally into ember-power-select/simple and ember-power-select/multiple
- [BUGFIX] Fix bug where dropdown didn't close when selecting an option inside a group.
- [BUGFIX] Fix ember-wormhole destination not being added to the body footer. Solved by calling contentFor of dependencies.
- [ENHANCEMENT] Update to ember-basic-dropdown 2.0. That yields a hash with public API on it.

# 0.2.0

- [BUGFIX] Fix compatibility with Ember 1.13 and add it to ember-try
- [ENHANCEMENT] Simplified code greatly by using ember-basic-dropdown underneath.
- [DOCS] Several typos
