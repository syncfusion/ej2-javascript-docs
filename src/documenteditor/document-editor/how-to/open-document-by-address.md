---
title: "How to"
component: "DocumentEditor"
description: "Learn how to open a document from URL in DocumentEditor"
---

# Open a document from URL

## How to open a document from URL in DocumentEditor

In this article, we are going to see how to open a document from URL in DocumentEditor

please refer below example for client-side code

```typescript

let container: DocumentEditorContainer = new DocumentEditorContainer();
container.appendTo('#DocumentEditorContainer');
document.getElementById('import').addEventListener('click', () => {
let http: XMLHttpRequest = new XMLHttpRequest();
let content = {fileUrl:""/*add your url in which you want to open document inside the ""*/};
let baseurl: string = hostUrl + "api/documenteditor/ImportFileURL";
http.open("POST", baseurl, true);
http.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
http.onreadystatechange = () => {
  if (http.readyState === 4) {
    if (http.status === 200 || http.status === 304) {
      // open SFDT text in document editor
      container.documentEditor.open(http.responseText);
    }
  }
};
http.send(JSON.stringify(content));
});

```

please refer below example for server-side code

```typescript

[AcceptVerbs("Post")]
public string ImportFileURL([FromBody]FileUrlInfo param)
 {
   try
     {
      using (WebClient client = new WebClient())
        {
             MemoryStream stream = new MemoryStream(client.DownloadData(param.fileUrl));
             WordDocument document = WordDocument.Load(stream, FormatType.Docx);
             string json = Newtonsoft.Json.JsonConvert.SerializeObject(document);
             document.Dispose();
             stream.Dispose();
             return json;
                }
            }
            catch (Exception)
            {
                return "";
            }
}
public class FileUrlInfo
        {
            public string fileUrl;
            public string Content { get; set; }
        }
  
```
