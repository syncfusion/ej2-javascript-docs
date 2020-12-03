---
title: "Different layouts"
component: "Splitter"
description: "This section explains about user can construct different layouts using mulitple and nested panes."
---

# Different layouts

By using splitter control, you can create the different layouts with multiple and nested panes.

## Code editor style layout

**Step 1** :

Create the element with two child to render the outer splitter.

```html
 <div id="VerticalSplitter">
            <div id="HorizontalSplitter">
            </div>
            <div>
                <div class="content">
                    <h3 class="h3">CSS</h3>
                    <div class="code-preview">
                        <span>img {</span>
                        <div id="code-text">margin:<span>0 auto;</span></div>
                        <div id="code-text">display:<span>flex;</span></div>
                        <div id="code-text">height:<span>70px;</span></div>
                        <span>   }</span>
                    </div>
                </div>
            </div>
</div>

```

```javascript

 var VerticalSplitObj = new ej.layouts.Splitter({
        height: '400px',
        paneSettings: [
            { size: '53%', min: '30%' }
        ],
        orientation: 'Vertical'
    });
VerticalSplitObj.appendTo('#splitter2');

```

**Step 2** :

Render the first pane of vertical splitter as a horizontal splitter.

```html
 <div id="VerticalSplitter">
            <div id="HorizontalSplitter">
                    <div>
                        <div class="content">
                            <h3 class="h3">HTML</h3>
                            <div class="code-preview">
                                &lt;<span>!DOCTYPE html></span>
                                <div>&lt;<span>html></span></div>
                                <div>&lt;<span>body></span></div>
                                &lt;<span>div</span> id="custom-image">
                                <div style="margin-left: 5px">&lt;<span>img</span>src="src/albert.png"></div>
                                <div>&lt;<span>div</span>&gt;</div>
                                <div>&lt;<span>/body></span></div>
                                <div>&lt;<span>/html></span></div>
                            </div>
                        </div>
                    </div>
                <div>
                    <div class="content">
                        <h3 class="h3">CSS</h3>
                        <div class="code-preview">
                            <span>img {</span>
                                <div id="code-text">margin:<span>0 auto;</span></div>
                                <div id="code-text">display:<span>flex;</span></div>
                                <div id="code-text">height:<span>70px;</span></div>
                            <span>   }</span>
                        </div>
                    </div>
                </div>
                <div>
                    <div class="content">
                        <h3 class="h3">JavaScript</h3>
                        <div class="code-preview">
                            <span>var</span> image = document.getElementById("custom-image");
                            <div>image.addEventListener("click", function() {</div>
                                <div style="padding-left: 20px;">// Code block for click action</div>
                            <span> }</span>
                        </div>
                    </div>
                </div>
            </div>
            <div class="content">
                <h3 class="h3">Preview of sample</h3>
                <div class="splitter-image">
                    <img class="img1" src="https://ej2.syncfusion.com/demos/src/listview/images/albert.png" style="width: 20%;margin: 0 auto;">
                </div>
            </div>
        </div>

```

```javascript

    var HorizontalSplitObj = new ej.layouts.Splitter({
        height: '220px',
        paneSettings: [
            { size: '29%', min: '23%' },
            { size: '20%', min: '15%' },
            { size: '35%', min: '35%' }
        ],
        width: '100%'
    });
    HorizontalSplitObj.appendTo('#splitter1');
```

```css
    .code-preview {
        margin-top: 15px;
        font-size: 12px;
    }
    .content {
        padding: 12px;
    }
    .splitter-image {
        margin: 0 auto;
        display: flex;
        height: 115px;
        margin-top: 10px;
    }

```

You can check the result [here](https://ej2.syncfusion.com/javascript/demos/#/material/splitter/code-editor-layout.html)

## Outlook style layout

**Step 1** :

Create the element with three panes and place the elements within the pane to render `treeview`, `listview` and `RTE`.

```html

 <div id="splitter1">
        <div>
            <div class="content">
                <div id="tree"></div>
            </div>
        </div>
        <div>
            <div class="content">
                <div id="groupedList" tabindex="1"></div>
            </div>
        </div>
        <div>
            <div class="content">
                <div style="width: 100%; padding: 15px;">
                    <table>
                        <tr>
                            <td><button class="e-btn e-flat e-outline">To...</button></td>
                            <td><input id="firstname" /></td>
                        </tr>
                        <tr>
                            <td><button class="e-btn e-flat e-outline">Cc...</button></td>
                            <td><input id="lastname" /></td>
                        </tr>
                        <tr>
                            <td><div id="subject-text">Subject</div></td>
                            <td><input id="subject" /></td>
                        </tr>
                    </table>
                </div>
                <div class="forum">
                    <div id="createpostholder">
                        <div id="defaultRTE"> </div>
                        <div id="buttonSection">
                            <button class="e-btn e-primary" id="send">Send</button>
                            <button class="e-btn" id="discard">Discard</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

```

**Step 2** :

Place the template script to render the treeview.

```javascript
<script id="treeTemplate" type="text/x-template">
    <div>
        <div class="treeviewdiv">
            <div style="float:left">
                <span class="treeName">${name}</span>
            </div>
            ${if(count)}
                <div style="margin-right: 5px; float:right">
                    <span class="treeCount e-badge e-badge-primary">${count}</span>
                </div>
            ${/if}
        </div>
    </div>
</script>

```

**Step 3** :

Render the listed controls one by one.

```javascript
       var splitObj1 = new ej.layouts.Splitter({
        height: '493px',
        paneSettings: [
            { size: '28%', min: '27%' },
            { size: '33%', min: '23%' },
            { size: '37%', min: '30%' }
        ],
        width: '100%'
    });
    splitObj1.appendTo('#splitter1');
    var inputobj1 = new ej.inputs.TextBox({});
    inputobj1.appendTo('#firstname');
    var inputobj2 = new ej.inputs.TextBox({});
    inputobj2.appendTo('#lastname');
    var inputobj3 = new ej.inputs.TextBox({});
    inputobj3.appendTo('#subject');
    // Data source for TreeView component
    var mailBox = [
        { id: 1, name: 'Favorites', hasChild: true },
        { id: 2, pid: 1, name: 'Sales Reports', count: '4' },
        { id: 3, pid: 1, name: 'Sent Items' },
        { id: 4, pid: 1, name: 'Marketing Reports ', count: '6' },
        { id: 5, name: 'Andrew Fuller', hasChild: true, expanded: true },
        { id: 6, pid: 5, name: 'Inbox', selected: true, count: '20' },
        { id: 7, pid: 5, name: 'Drafts', count: '5' },
        { id: 15, pid: 5, name: 'Archive' },
        { id: 8, pid: 5, name: 'Deleted Items' },
        { id: 9, pid: 5, name: 'Sent Items' },
        { id: 10, pid: 5, name: 'Sales Reports', count: '4' },
        { id: 11, pid: 5, name: 'Marketing Reports', count: '6' },
        { id: 12, pid: 5, name: 'Outbox' },
        { id: 13, pid: 5, name: 'Junk Email' },
        { id: 14, pid: 5, name: 'RSS Feed' },
        { id: 15, pid: 5, name: 'Trash' }
    ];
    // Render the TreeView using template option
    var treeObj = new ej.navigations.TreeView({
        fields: { dataSource: mailBox, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild' },
        nodeTemplate: '#treeTemplate',
    });
    treeObj.appendTo('#tree');
    // tslint:disable:max-line-length
    //Define an array of JSON data
    var dataSource = [
        { Name: 'Selma Tally', content: '<div><div class="status">Apology marketing email</div><div id="list-message">Hello Ananya Singleton</div>', id: '1', order: 0 },
        { Name: 'Illa Russo', content: '<div><div class="status">Annual conference</div><div id="list-message">Hi jeani Moresa</div></div>', id: '4', order: 0 },
        { Name: 'Camden Macmellon', content: '<div><div class="status">Reference request- Camden hester</div><div id="list-message">Hello Kerry Best,</div></div>', order: 0 },
        { Name: 'Garth Owen', content: '<div><div class="status">Application for job Title</div><div id="list-message">Hello Illa Russo</div></div>', id: '2', order: 0 },
        { Name: 'Ursula Patterson', content: '<div><div class="status">Programmaer Position Applicant</div><div id="list-message">Hello Kerry best,</div></div>', id: '2', order: 0 }
    ];
    // Initialize ListView component
    var listObj = new ej.lists.ListView({
        //Set defined data to dataSource property
        dataSource: dataSource,
        cssClass: 'e-list-template',
        //Map the appropriate columns to fields property
        fields: { text: 'Name', groupBy: 'order' },
        //Set customized group-header template
        groupTemplate: '<div class="e-list-wrapper"><span class="e-list-item-content"></span></div>',
        //Set customized list template
        template: '<div class="settings e-list-wrapper e-list-multi-line e-list-avatar">' +
            '<span class="e-list-item-header">${Name}</span>' +
            '<span class="e-list-content">${content}</span>' +
            '</div>'
    });
    //Render initialized ListView component
    listObj.appendTo('#groupedList');
    var button1 = new ej.buttons.Button({ isPrimary: true });
    button1.appendTo('#rteSubmit');
    var button2 = new ej.buttons.Button();
    button2.appendTo('#rteCancel');
    var defaultRTE = new ej.richtexteditor.RichTextEditor({ height: '262px' });
    defaultRTE.appendTo('#defaultRTE');

```

```css
  <style>
    #target {
        margin: 20px auto;
        max-width: 820px;
    }
    .e-treeview .e-list-text {
        width: 100%;
    }
    #groupedList.e-listview .e-list-group-item {
        height: 0;
    }
    #splitter1 .settings.e-list-wrapper.e-list-multi-line.e-list-avatar {
        padding: 15px;
    }
    #buttonSection {
        padding: 7px;
    }
</style>
```

Once the above configurations has been completed, you will get the output like [this](https://ej2.syncfusion.com/javascript/demos/#/material/splitter/outlook-style-layout.html).

## See Also

* [Multiple panes in Splitter](./es5-split-panes/)