---
title: "Test-Helper Apis"
component: "TreeGrid"
description: "Learn what are the testing helper api's available in EJ2 Tree Grid component and how to use them to test the component using cypress application."
---
# Helper APIs

Essential JS 2 components packages provide the testing helper APIs for testing the Essential JS 2 components. The following helper APIs are available for the Tree Grid component’s testing helpers in Essential JS 2.

|    Helper Methods          |               Description                            |
|:--------------------:|---------------------|
| getTreeGridElement | This function helps you to get the treegrid element of the Tree Grid.<br/><br/>**Syntax**: `curObj.getTreeGridElement()` |
| getHeaderElement | This function helps you to get the header element of the Tree Grid.<br/><br/>**Syntax**: `curObj.getHeaderElement()` |
| getContentElement | This function helps you to get the content element of the Tree Grid.<br/><br/>**Syntax**: `curObj.getContentElement()` |
| getFooterElement | This function helps you to get the footer element of the Tree Grid when Aggregates are enabled.<br/><br/>**Syntax**: `curObj.getFooterElement()` |
| getPagerElement | This function helps you to get the pager element of the Tree Grid when paging feature is enabled.<br/><br/>**Syntax**: `curObj.getPagerElement()` |
| getFilterPopUpElement | This function helps you to get the Filter Dialog element of the Columns in Tree Grid.<br/><br/>**Syntax**: `curObj.getFilterPopUpElement()` |
| getDialogElement | This function helps you to get the Edit Dialog element of Tree Grid when the Edit Mode is Dialog.<br/><br/>**Syntax**: `curObj.getDialogElement()` |
| getCurrentPagerElement | This function helps you to get the current page indicator element of the Tree Grid.<br/><br/>**Syntax**: `curObj.getCurrentPagerElement()` |
| getPagerDropDownElement | This function helps you to get the page size dropdownlist element of the TreeGrid.<br/><br/>**Syntax**: `curObj.getPagerDropDownElement()` |
| getExpandedElements | This function helps you to get all the expanded icon elements in the current page of Tree Grid.<br/><br/>**Syntax**: `curObj.getExpandedElements()` |
| getCollapsedElements | This function helps you to get all the collapsed icon elements in the current page of Tree Grid.<br/><br/>**Syntax**: `curObj.getCollapsedElements()` |