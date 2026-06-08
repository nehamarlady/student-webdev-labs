## Code Review Exercise

## Issue 1: Submit and Reset button are outside the form

When submit and reset is clickedd after filling, nothing happens.
Since the buttons are outside the form: submit will not submit the form, reset will not clear the form fields and user may think the webiste is broken.

This is a semantic HTML and functionality issue

Initial code:

<form id="RequestInfo" class="content-container form">
....
</form>

<div
        class="form space-evenly-distributed-row-container form-buttons-container"
      >
        <input class="form-button" type="submit" value="submit" />
        <input class="form-button" type="reset" value="reset" />
      </div>

Solution:
Move the buttons inside the form.

Updated code:

<form id="RequestInfo" class="content-container form">
  ...

  <div class="form-buttons-container">
    <input type="submit" value="Submit">
    <input type="reset" value="Reset">
  </div>
</form>


## Issue 2: More Infor Uses Anchor Instead of Button
When we hover over a More info Control. it behaves like a button and opens a popup. it does not navigate anywhere. An anchor elements is being used as a button.
Anchor should navigate to another page and open a URL
Buttons should triggers actions , open popups and submits forms.
Using an anchor for an action confuses screen reader and hurts the accessibility and viloates semantics html peinciples.

Initial code:
<a class="more-info-button">
  More Info
</a>

Solution: use a button elements 

updated code:
<button class="more-info-button">
  More Info
</button>

## Issue 3: Form lables not associated with inputs
when the word "Name" or any another input fields in the forms. The cursor should move into the textbox. but it does not.

Initial code:
<span class="form-label">
  Name
</span>

<input
  id="name"
  type="text"
/>

Solution:
Replace span with label and connect it using the imput id
updated code:

<label
  class="form-label"
  for="name"
>
  Name
</label>

<input
  id="name"
  type="text"
/>

## Issue 4: Typo in CSS variable name --darker-blue-transpaent

The CSS custom variable is mispelled as --darker-blue-transpaent

Typos in CSS variable names can lead to:
Styles not being applied correctly. Other developers becoming confused about which variable to use. Inconsistencies when referencing the variable elsewhere in the stylesheet. Increased maintenance difficulty because the typo may be copied throughout the codebase.

Initial code:
:root {
  --darker-blue-transpaent: rgba(0, 0, 139, 0.5);
}

.card {
  background-color: var(--darker-blue-transpaent);
}

Updated code:
:root {
  --darker-blue-transparent: rgba(0, 0, 139, 0.5);
}

.card {
  background-color: var(--darker-blue-transparent);
}

## Issue 5: Missing Fieldset for checkbox groupd

The checkbox options represent a single question "which cat breeds do you like?", but they are not enclosed withing a fildset element and do not have a <legend> describing the group.

Current code:
<div class="checkbox-container">
  <input type="checkbox" id="persian" name="breed1">
  <label for="persian">Persian</label>

  <input type="checkbox" id="siamese" name="breed2">
  <label for="siamese">Siamese</label>

  <input type="checkbox" id="mainecoon" name="breed3">
  <label for="mainecoon">Maine Coon</label>

  <input type="checkbox" id="bengal" name="breed4">
  <label for="bengal">Bengal</label>
</div>

Updated code:
<fieldset class="checkbox-container">
  <legend>Favorite Cat Breeds</legend>

  <input type="checkbox" id="persian" name="breeds[]">
  <label for="persian">Persian</label>

  <input type="checkbox" id="siamese" name="breeds[]">
  <label for="siamese">Siamese</label>

  <input type="checkbox" id="mainecoon" name="breeds[]">
  <label for="mainecoon">Maine Coon</label>

  <input type="checkbox" id="bengal" name="breeds[]">
  <label for="bengal">Bengal</label>
</fieldset>
