sass-css-utilities - A SASS library for rapid frontend development.
==============

## Intro

The main aim of the library is to speedup up the website development process with the usage of simple utility classes.
The utility classes can be used to modify web page elements in `tablets` and `phones` without needing to make any CSS changes.

It also contains a small set of useful SASS mixins.

## Class names

All of the CSS classes support usage in phones and tables through media queries. You simply need to add the device category specific prefix to make them device specific. The default prefixes are: `tab-`, `phn-tab-`, `phn-` (These can be changed in config)

For example, For  modifying the display property of a div in different devices:

    <div class="block phn-inline-block">I will change to inline block when viewed on a phone</div>

Similarly for changing margin or padding:

    <div class="pad-30 mar-60 tab-pad-20 tab-mar-40 phn-pad-10 phn-mar-20">My margin and padding will change in tablet and phone</div>

This is just a simple example. The classes can be used to modify even a single property like this:

    <div class="pad-30 mt-60 phn-pv-20 phn-mt-20">My top margin and vertical padding will change in phone</div>


----------
## Documentation

### Utility classes

#### Floats
 - `fl` : Float left
 - `fr` : Float right
 - `clr` or `clear` : Clear both

#### Text Align
 - `ta-c` or `align-center` : Text align center
 - `ta-l` or `align-left` : Text align left
 - `ta-r` or `align-right` : Text align right

#### Vertical Align
 - `va-t` or `align-top` : Vertical align top
 - `va-m` or `align-middle` : Vertical align middle
 - `va-b` or `align-bottom` : Vertical align bottom

#### Appearance
 - `is-hidden` : display:none
 - `is-invisible` : visibility: hidden
 - `is-transparent` : opacity 0
 - `is-opaque` : opacity 1
 - `block` : display:block
 - `inline-block` : display:inline-block
 - `border-box` : border-box box model

#### Text Utilities
 - `hide-text` : Hides text using text-index technique
 - `ellipsis` : Truncates text with ellipsis
 - `non-selectable` or `disable-text-select` : Disables text selection
 - `uc` or `uppercase` : Transforms text to uppercase
 - `lc` or `lowercase` : Transforms text to lowercase

#### Position
 - `pos-relative` : Relative position
 - `pos-absolute` : Absolute position
 - `pos-fixed` : Fixed position
 - `pos-static` : Static position

#### Interaction
 - `clickable` : cursor:pointer; (Add adjacent class `disabled` to disable it for the element)

----------
### Utility SASS mixins (Cross-browser and No dependencies)

#### Border radius
 - `border-radius($radius)`
 - `border-radius-top-left($radius)`
 - `border-radius-top-right($radius)`
 - `border-radius-bottom-left($radius)`
 - `border-radius-bottom-right($radius)`

#### Media queries
 - `at-least-width($device-width)` : Devices with min width as specified
 - `until-width($device-width)` : Devices with max width as specified
 - `if-device($device)` : Media query specific to a device. Possible values are `tablet`, `phone-tablet` and `phone`.

Device width config can be updated in these variables:
```
$config-phone-max-width   : 767px;
$config-tablet-min-width  : 768px;
$config-tablet-max-width  : 979px;
$config-desktop-min-width : 980px;
```

#### Example Usage
```
@include at-least-width(979px){
    ...
}
@include if-device(phone){
    ...
}
```

#### Shadow
 - `box-shadow($params)` : Example: @include box-shadow(2px 2px 2px 0 #000);
 - `text-shadow($params)`

#### Font size and line height
 - `font-size($size, $line_height)` : Converts to rem values + provides px values as fallback. Line height is optional. Example usage: `@include font-size(12,18);`

### Margin
`ma` or `mar-auto` : Auto value for left and right margin. (margin-left:auto; margin-right:auto;)

`ml-a` or `ml-auto`: `auto` value for left margin property

`mr-a` or `mr-auto`: `auto` value for right margin property

#### Auto generated margin classes:
Specify values of margins to be generated in variable `$config-margins` and the library will automatically generate different cases based on these. 

    $config-margins: (0 5 10 15 20)

Properties available are (where `X` is one of the values passed in `$config-margins`

`mar-X` : Margin X. Eg: mar-5 is margin: 5px;

`mt-X` : Top Margin. Eg: mt-10 is margin-top: 10px;

`mb-X` : Bottom Margin. Eg: mb-10 is margin-bottom: 10px;

`ml-X` : Left Margin. Eg: ml-10 is margin-left: 10px;

`mr-X` : Right Margin. Eg: mr-10 is margin-right: 10px;

`mv-X` : Vertical Margin. Eg: mv-5 is margin-top: 5px; margin-bottom: 5px;

`mh-X` : Horizontal Margin. Eg: mh-5 is margin-left: 5px; margin-right: 5px;

### Padding
Padding classes are also auto generated just like the margin classes.

`pad-X` : Padding X. Eg: pad-5 is padding: 5px;

`pt-X` : Top Padding. Eg: pt-10 is padding-top: 10px;

`pb-X` : Bottom Padding. Eg: pb-10 is padding-bottom: 10px;

`pl-X` : Left Padding. Eg: pl-10 is padding-left: 10px;

`pr-X` : Right Padding. Eg: pr-10 is padding-right: 10px;

`pv-X` : Vertical Padding. Eg: pv-5 is padding-top: 5px; padding-bottom: 5px;

`ph-X` : Horizontal Padding. Eg: ph-5 is padding-left: 5px; padding-right: 5px;

### Tablet and Mobile
Both padding and margins of an element can be changed in different devices by using them with device specific prefix. For example:

    <div class="pad-40 tab-pad-30 phn-pad-20 phn-pt-10">Content</div>
This div will have `40px` padding in desktop, `30px` padding in tablets and `20px` padding in phones. Additionally we have further changes the top padding to `10px` in phone.

### Custom values
The classes to be generated can be specified in variables `$config-paddings` and `$config-margins`. The default values are:

    $config-paddings: (0 5 10 15 20 25 30);
    $config-margins:  (0 5 10 15 20 25 30);

MORE DOCS COMING SOON!
