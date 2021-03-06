YIKES Inc. Easy Forms for MailChimp
=====================

[![WordPress](https://img.shields.io/wordpress/plugin/dt/yikes-inc-easy-mailchimp-extender.svg)]()
![Rating](https://img.shields.io/wordpress/plugin/r/yikes-inc-easy-mailchimp-extender.svg)
[![License](https://poser.pugx.org/yikesinc/yikes-inc-easy-mailchimp-extender/license)](https://packagist.org/packages/yikesinc/yikes-inc-easy-mailchimp-extender)
![WordPress plugin](https://img.shields.io/wordpress/plugin/v/yikes-inc-easy-mailchimp-extender.svg)
![WordPress](https://img.shields.io/wordpress/v/yikes-inc-easy-mailchimp-extender.svg)

This version (Version 6) is a complete re-write of the original [YIKES Inc Easy MailChimp Extender](https://wordpress.org/plugins/yikes-inc-easy-mailchimp-extender/) plugin.


#### Minimum Requirements
- WordPress 3.8+ 
- PHP v5.3+

#### Plugin Screenshots
[Cloudup Gallery](https://cloudup.com/cyfImk387Ez)


#### Documentation

For full documentation, please visit [our Knowledge Base](https://yikesinc.freshdesk.com/support/solutions/6000083118).


#### Questions?
Have any questions? Feel free to open up an issue in the issue tracker and we'll get back to you as soon as possible.

<hr />
 
#### Grunt.js

To develop with grunt place Gruntfile.js file inside the plugin root during development (/wp-content/yikes-inc-easy-mailchimp-extender/). The paths inside Gruntfile.js are setup relative to the plugin root, so placing it anywhere else without changing the paths will cause an error.

To install the required dependencies we've included an [auto_install](https://www.npmjs.com/package/grunt-auto-install) tasks to make your life easier. 

First, make sure you install the latest version of Grunt to the local project directory.

```bash
$ npm install -g grunt -cli
```

```bash
$ npm install grunt
```

Then install autoprefixer-core and the auto_install plugins using:

```bash
$ npm install autoprefixer-core --save-dev
```

```bash
$ npm install grunt-auto-install --save-dev
```

Finally, run the [auto_install](https://www.npmjs.com/package/grunt-auto-install) task to install the required dependencies.

```bash
$ grunt auto_install
```


##### Shortcode

`[yikes-mailchimp form="#"]`

##### Full List of Shortcode Parameters
- form - the ID of the form you want to display *(required)*
- submit - the text of the submit button below the form *(optional - defaults to "Submit")*
- title - display the title above the form (1 or 0) *(optional - defaults to 0)*
- description - display the description above the form (1 or 0) *(optional - defaults to 0)*

##### CSS Ready Classes

###### 2 Column Layout
- field-left-half / field-right-half - assign this class to place the field in the left/right column of a 2 column form layout.

###### 3 Column Layout
- field-left-third / field-right-third - assign this class to place the field in the left/right most column of a 3 column form layout. 

###### 2/3/4 Colum Radio Buttons
- option-2/3/4-col - split the radio or checkbox options into 2, 3 or 4 columns


##### Filters + Hooks

###### Filters
- yikes-mailchimp-form-title-FORM_ID - alter the output of the form title of the specified form
- yikes-mailchimp-form-description-FORM_ID - alter the output of the form description of the specified form
- yikes-mailchimp-redirect-timer (ms : 1 second = 1000ms) alter the amount of time the user sees the success message before being redirected (default: 1500ms) (@parameters - $time, $form_id)
- yikes-mailchimp-redirect-url - Alter the URL of the page that the user will be redirected too on a successful submission. (@parameters - $url, $form_id, $page_data)
- yikes-mailchimp-before-submission - catch the merge variables of all forms before they get sent over to MailChimp
- yikes-mailchimp-before-submission-FORM_ID - catch the merge variables of the specified form before they get sent over to MailChimp
- yikes-mailchimp-after-submission - catch the merge variables of all forms after they get sent over to MailChimp
- yikes-mailchimp-after-submission-FORM_ID - catch the merge variables of the specified form after they get sent over to MailChimp
- yikes-mailchimp-user-role-access - Alter who can access this plugin page by capability (default 'manage_options' - admins)
- yikes-mailchimp-international-phone-pattern - Alter the regex pattern for acceptable international phone number formats. (process form shortcode.php - line 295)
- yikes-mailchimp-us-phone-pattern - Alter the regex pattern for acceptable US phone number formats. (process form shortcode.php - line 295)
- yikes-mailchimp-process-default-tag - Pass the default tag through a filter to populate with dynamic content from the current site (process_form_shortcode.php - line 256)
- yikes-mailchimp-MERGE_TAG-label - Alter the specified field label text (affects standard fields & interest groups) (process_form_shortcode.php) 
- yikes-mailchimp-address-TYPE-label - Alter the field sub-label text for a specified address field (affects only standard address fields) (process_form_shortcode.php) 
- yikes-mailchimp-form-submit-button - Alter the submit button to your liking (process_form_shortcode.php line 660) (@parameters - $submit_button, $form_id)
- yikes-mailchimp-form-submit-button-text - Alter the submit button text value (process_form_shortcode.php line 660) (@parameters - $submit_button_text, $form_id )
- yikes-mailchimp-form-container-class - add additional classes to the parent form container (process_form_shortcode.php line157) (@parameters - $content, $form_id)
- yikes-mailchimp-form-class - add additional classes to <form> element of your opt-in form (process_form_shortcode.php line157) (@parameters - $content, $form_id)
- yikes-mailchimp-front-end-form-action-links - Add custom front end action links alongside Edit Form, Customize Form etc. (@parameters - $form_action_links, $form_id, $form_name)
- yikes-mailchimp-custom-default-value-tags - Define your own custom pre-defined tags to populate the default value fields with - these tags appear in the modal - (@parameters - $pre_defined_tags_array)
- yikes-mailchimp-parse-custom-default-value - Process your custom default merge tag into a custom value to populate the form field with - (Goes hand in hand with `yikes-mailchimp-custom-default-value-tags` filter)
- yikes-mailchimp-field-data - Filter form field data such as placeholder, label, etc. (@parameters - $field_array, $field, $form_id) (process_form_shortcode.php - line 258 & process_preview_form_shortcode.php - line 258)
- yikes-mailchimp-subscriber-count-value - Adjust the returned value for the total subscriber count of a given MailChimp mailing list as needed. (@parameters - $subscriber_count) (yikes-mailchimp-subscriber-count.php- line 80)

###### Hooks
- yikes-mailchimp-form-submission - do something with the user email + form data on form submission
- yikes-mailchimp-form-submission-FORM_ID - do something with the user email + form data on form submission (specific form)
- yikes-mailchimp-before-form - output content before all forms (@parameters - $form_id)
- yikes-mailchimp-after-form - output content after all forms (@parameters - $form_id)
- yikes-mailchimp-before-checkbox - output custom content before the opt-in checkbox for all integrations
- yikes-mailchimp-after-checkbox - output custom content after the opt-in checkbox for all integrations
- yikes-mailchimp-support-page - output custom content on the support page (used to add our support form for premium users)
- yikes-mailchimp-edit-form-section-links - add additional links to the edit form page next to 'Custom Messages'
- yikes-mailchimp-edit-form-sections - add custom section to the edit form page
- yikes-mailchimp-edit-form-notice - hook to display a custom notice on the edit form page 
- yikes-mailchimp-shortcode-enqueue-scripts-styles - hook to enqueue custom scripts & styles wherever the shortcode is being used (@paremeter $form_id - pass the id of the current form)
- yikes-mailchimp-additional-form-fields - define additional fields to add below all forms (@parameter $form_data - all data associated with the given form)
- yikes-mailchimp-custom-form-actions - add custom action links on the manage forms page (alongside Edit, Duplicate, Shortcode, Delete ) (@parameter $form_id - the id of the form)

###### Hooks for Extensions
- yikes-mailchimp-menu - hook to add additional menu items inside of the "Easy MailChimp" menu item
- yikes-mailchimp-settings-field - hook to register additional settings fields for add-ons
- yikes-mailchimp-ADDON-SLUG-options-path - hook to load up a custom settings page

##### Helper Shortcodes

<strong>Display current number of subscribers</strong>
`[yikes-mailchimp-subscriber-count form="1"]` 

Display the current number of subscribers for a given list. Pass in the form ID whos list you want to display. (also accepts list="mailchimp_list_id")

If you want to use the snippet inside of your form description, you can exclude the form ID and list ID altogether, and the shortcode will reference the list associated with the displayed form.

Example Form Description:
Join the `[yikes-mailchimp-subscriber-count]` happy subscribers who receive our mailing list!

which might display on the front end like:
Join the 1,543 happy subscribers who receive our mailign list!

###	Custom Edit Form Sections API
Since we've built out a few add-ons to extend the base functionality, we've also built out an API to allow users to rapidly define custom sections on the edit form screen. This allows you to assign additional data to your forms.

We use this API extensively to build out additional sections on the edit form page.

Example:

<em>First hook in to the proper locations, and attach a function:</em>
```php
add_action( 'yikes-mailchimp-edit-form-section-links' , 'add_custom_section_link' );
add_action( 'yikes-mailchimp-edit-form-sections' , 'render_custom_section' );
```
<em>Next , define your sections and fields by passing in a multi-dimensional array.</em>
```php
/* Add custom link to the links (next to fields & custom messages) */
public function add_custom_section_link() {
	// creating a new link on the edit form page
	Yikes_Inc_Easy_Mailchimp_Extender_Helper::add_edit_form_section_link( array(
		'id' => 'custom-section', // section id
		'text' => 'Custom Section', // the text that will display in the link
		'icon' => 'admin-appearance' // dashicon icon class
	) );
		
	// creating a new link on the edit form page
	Yikes_Inc_Easy_Mailchimp_Extender_Helper::add_edit_form_section_link( array(
		'id' => 'custom-section-2', // section id
		'text' => 'Custom Section 2', // the text that will display in the link
		'icon' => 'admin-appearance' // dashicon icon class
	) );
}
	
/* Add custom section associated with link created above */
public static function render_custom_section() {
	// defining a new section, associated with the link above
	Yikes_Inc_Easy_Mailchimp_Extender_Helper::add_edit_form_section( array(
		'id' => 'custom-section',  // section id (must match link id above)
		'main_title' => 'Main Section Title', // title of the main block of this custom section
		'main_description' => __( 'This is a custom description for the main section' , 'test' ),
		'main_fields' => array(
			array(
				'label' => 'Custom Field #1', // label text for this field
				'placeholder' => 'Placeholder Value',  // placeholder value for the input field
				'type' => 'text', // type of field (text,select,checkbox,radio)
				'id' => 'custom-field-1', // field id - determines how data is saved in database
				// 'description' => __( 'Testing custom description for field #1' , 'test' ), // field description
			),
			array(
				'label' => 'Custom Field #2', // label text for this field
				'placeholder' => 'Placeholder Value #2', // placeholder value for the input field
				'type' => 'text', // type of field (text,select,checkbox,radio)
				'id' => 'custom-field-2', // field id - determines how data is saved in database
				'description' => __( 'Testing custom description for field #2' , 'test' ), // field description
			),
		),
		'sidebar_title' => 'Sidebar Section Title', // sidebar title of the sidebar section
		'sidebar_description' => __( 'This is a custom description for the sidebar section' , 'test' ),
		'sidebar_fields' => array(
			array(
				'label' => 'Dropdown Field',
				'type' => 'select',
				'options' => array(
					'1' => 'one',
					'2' => 'two',
					'3' => 'three',
				),
				'id' => 'select-field',
				'description' => __( 'this is a select field.' , 'test' ),
			),
		),
	) );
}
```