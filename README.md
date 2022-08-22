# RLPath
RL job automation by using UiPath

## Notes
* Better use browser in Incognito mode, always open and close. Because if the browser profile changes, the program may fail.
* Use arguments to communicate between projects(different sequence files)
* Assign the value to the out argument of the sub project, import the augument into main project and assign the augument value to a variable so that you can use it from main. 

## Design
### Processes Completed Answers
* Get "Yes / No" radio button icon ID
* Find Element Activity: 
  * Selector: "<webctrl id='ctl00_ctl00_MainContent_PageMainContent_popupControlServiceReasons_ucProcessComplete_gvServicesPerformed_cell11_0_rblYesNo_RB1_I_D' />"
  * FoundElement: TheElement
* Get Attribute Activity
  * Attribute: "class"
  * Save to: TheClass
* Check the enable/disable status from the class:
  * Enable: class="dxEditors_edtRadioButtonChecked_Aqua dxeIRadioButton_Aqua dxichSys"
  * Disable: class=" dxeIRadioButton_Aqua dxichSys dxEditors_edtRadioButtonUnchecked_Aqua"
  * Enable => "RadioButtonChecked" or Disable => "RadioButtonUnchecked"
* Click Activity: click the (Yes/No)element to select it.

