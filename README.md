# Crocoblocks JetFormBuilder Password Strength

Via this code you can add a password strength meter to forms which contain password fields. For example in the screenshot below you can see that I have entered a very weak password. The code also disables the Submit button until a strong password has been entered, and the password check field also matches that password.

![Example frontend](https://user-images.githubusercontent.com/124208724/216170611-0fb2a756-208f-4175-8876-cc7fc7fbe3fc.png)

### 1. Add to functions.php in your (child) theme
1. Add the following code to your functions.php file: `wp_enqueue_script( 'password-strength-meter' );`
2. Save the file

### 2. Add to JetFormBuilder
1. Go to JetFormBuilder
2. Create a new registration form (https://jetformbuilder.com/features/wordpress-register-form-creation/) or edit an existing registration form which you have made earlier
3. Add 2 text fields to the form
4. Edit both fields and set:
- add a field label for both fields, name them for example Password and Password check
- add a form field name for the first field to for example: password
- add a form field name for the second field to for example: password-check
- set the Field type to Password for both fields
5. Add a HTML field to the form, this will be where the password strength meter is shown
6. Insert this code to the HTML field: `<span id="password-strength"></span>`
7. Save the form
![JetFormBuilder form setup](https://user-images.githubusercontent.com/124208724/216170675-7286fe73-fbfd-4844-8c07-3e9231a5847e.png)


### 3. Add to Elementor code
1. In the Wordpress backend, go to Elementor
2. Click on Custom Code in the menu
3. Add a new code
4. At location, choose </body> - End
5. At the content, add the full content from this file: https://github.com/jzelle/crocoblocks-jetformbuilder-passwordstrength/blob/main/Add%20to%20Elementor%20code.js
6. If you have entered other field names at JetFormBuilder: modify line 43, 46 and 47 with the name of your password fields, which are the names you have entered at Form field name in JetFormBuilder
7. Choose if necessary the condition for this code, so that it only loads on the page where the registration form is which you made with JetFormBuilder
8. Click on Update
![Elementor code setup](https://user-images.githubusercontent.com/124208724/216170646-a9c43aea-ded4-43e7-b9ed-86b3d5d552f4.png)


Now check the frontend where the form is placed :)



### Enhancements possible

Make the strength visible as colors
1. Edit your custom.css file (or somewhere else)
2. Add the following code which will display the password strenght in color to the user
`.bad, .short {
    color: red;
}
.good, .strong {
    color: green;
}`

Hide the submit button to show when the password fields have been filled
1. Edit the form
2. Add a conditional block (https://crocoblock.com/knowledge-base/articles/jetformbuilder-conditional-visibility-for-form-fields/)
3. Configure the conditional block so that it will hide when the password fields are empty
4. Save the form

Set the strength on which the submit button will be active
1. Go to the Elementor code which you have added
2. At line 36, change the number 3 to the strength you prefer. For example 4 = strong, you can see these numbers at line 18-25
3. Save the code

Add blacklisted words to the validation
1. Go to the Elementor code which you have added
2. At line 50, add extra words by adding the following to the array: , 'xxx'
3. Save the code


### Source
Code has been modified from this article to work with JetFormBuilder: https://code.tutsplus.com/articles/using-the-included-password-strength-meter-script-in-wordpress--wp-34736
