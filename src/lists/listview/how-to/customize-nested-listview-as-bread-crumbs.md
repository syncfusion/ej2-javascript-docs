# Customize Nested ListView as BreadCrumbs

ListView header can be customized using [headerTemplate](https://ej2.syncfusion.com/documentation/api/list-view/#headertemplate) property. Here We customized the header of nested ListView as BreadCrumbs with headerTemplate property . i.e while navigating to child data of a list item, the header data is customized with the selected data path.
For example, the header of nested ListView is Continent. While selecting a list item(Asia) then the header will be customized as Continent>Asia.

* This customization achieved while front and back navigations of list items with `actionComplete` event of ListView.
* On actionComplete we append the selected text in header element.
* And in back navigation, we removed the last appended span from header template

And also we can able to navigate the desired child level by clicking list items appended in the customized header. For example, let consider header of nested ListView is `Continent>Asia>India`. If we want to navigate to Continent level of ListView, then we can click the Continent in Header

N> In each navigation we have calculated the appended span tag length in `calculateLevelForElements` method to update header.

{% tab template="listview/bread-crumbs", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="bread-crumbs-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

//define the array of JSON
let continent: { [key: string]: Object }[] = [
    {
        'text': 'Asia',
        'id': '01',
        'category': 'Continent',
        'child': [{
            'text': 'India',
            'id': '1',
            'category': 'Asia',
            'child': [{
                'text': 'Delhi',
                'id': '1001',
                'category': 'India',
            },
            {
                'text': 'Kashmir',
                'id': '1002',
                'category': 'India',
            },
            {
                'text': 'Goa',
                'id': '1003',
                'category': 'India',
            },
            ]
        },
        {
            'text': 'China',
            'id': '2',
            'category': 'Asia',
            'child': [{
                'text': 'Zhejiang',
                'id': '2001',
                'category': 'China',
            },
            {
                'text': 'Hunan',
                'id': '2002',
                'category': 'China',
            },
            {
                'text': 'Shandong',
                'id': '2003',
                'category': 'China',
            }]
        }]
    },

    {
        'text': 'North America',
        'id': '02',
        'category': 'Continent',
        'child': [{
            'text': 'USA',
            'id': '3',
            'category': 'North America',
            'child': [{
                'text': 'California',
                'id': '3001',
                'category': 'USA',
            },
            {
                'text': 'New York',
                'id': '3002',
                'category': 'USA',
            },
            {
                'text': 'Florida',
                'id': '3003',
                'category': 'USA',
            }]
        },
        {
            'text': 'Canada',
            'id': '4',
            'category': 'North America',
            'child': [{
                'text': 'Ontario',
                'id': '4001',
                'category': 'Canada',
            },
            {
                'text': 'Alberta',
                'id': '4002',
                'category': 'Canada',
            },
            {
                'text': 'Manitoba',
                'id': '4003',
                'category': 'Canada',
            }]
        }]
    },

    {
        'text': 'Europe',
        'id': '03',
        'category': 'Continent',
        'child': [{
            'text': 'Germany',
            'id': '5',
            'category': 'Europe',
            'child': [{
                'text': 'Berlin',
                'id': '5001',
                'category': 'Germany',
            },
            {
                'text': 'Bavaria',
                'id': '5002',
                'category': 'Germany',
            },
            {
                'text': 'Hesse',
                'id': '5003',
                'category': 'Germany',
            }]
        }, {
            'text': 'France',
            'id': '6',
            'category': 'Europe',
            'child': [{
                'text': 'Paris',
                'id': '6001',
                'category': 'France',
            },
            {
                'text': 'Lyon',
                'id': '6002',
                'category': 'France',
            },
            {
                'text': 'Marseille',
                'id': '6003',
                'category': 'France',
            }]
        }]
    },
    {
        'text': 'Australia',
        'id': '04',
        'category': 'Continent',
        'child': [{
            'text': 'Australia',
            'id': '7',
            'category': 'Australia',
            'child': [{
                'text': 'Sydney',
                'id': '7001',
                'category': 'Australia',
            },
            {
                'text': 'Melbourne',
                'id': '7002',
                'category': 'Australia',
            },
            {
                'text': 'Brisbane',
                'id': '7003',
                'category': 'Australia',
            }]
        }, {
            'text': 'New Zealand',
            'id': '8',
            'category': 'Australia',
            'child': [{
                'text': 'Milford Sound',
                'id': '8001',
                'category': 'New Zealand',
            },
            {
                'text': 'Tongariro National Park',
                'id': '8002',
                'category': 'New Zealand',
            },
            {
                'text': 'Fiordland National Park',
                'id': '8003',
                'category': 'New Zealand',
            }]
        }]
    },
    {
        'text': 'Africa',
        'id': '05',
        'category': 'Continent',
        'child': [{
            'text': 'Morocco',
            'id': '9',
            'category': 'Africa',
            'child': [{
                'text': 'Rabat',
                'id': '9001',
                'category': 'Morocco',
            },
            {
                'text': 'Toubkal',
                'id': '9002',
                'category': 'Morocco',
            },
            {
                'text': 'Todgha Gorge',
                'id': '9003',
                'category': 'Morocco',
            }]
        }, {
            'text': 'South Africa',
            'id': '10',
            'category': 'Africa',
            'child': [{
                'text': 'Cape Town',
                'id': '10001',
                'category': 'South Africa',
            },
            {
                'text': 'Pretoria',
                'id': '10002',
                'category': 'South Africa',
            },
            {
                'text': 'Bloemfontein',
                'id': '10003',
                'category': 'South Africa',
            }]
        }]
    }
];

let text:string, backBtn:HTMLElement, title, headerElement, hasChild = false;

//Initialize ListView component
let listviewInstance = new ListView({
  //set the data to dataSource property
  dataSource: continent,
  // map the groupBy field with category column
  fields: { tooltip: "text" },
  headerTemplate: '<div class="header-content"><span>Continent</span></div>',
  showHeader: true,
  select: onSelect,
  actionComplete: onComplete
});
//Render initialized ListView
listviewInstance.appendTo("#listview");

backBtn = document.querySelector(".e-but-back") as HTMLElement;
title = document.querySelector(".header-content");
title.addEventListener("click", navigateBack);

function onSelect(e:any) {
  text = e.text;
  hasChild = !e.item.classList.contains("e-has-child");
}

function onComplete() {
  if (!hasChild) {
    headerElement = document.querySelector(".header-content").innerHTML;
    title = document.querySelector(".nested-header .header-content");
    if (headerElement && text != undefined) {
      // Create element with new clicked item in header
      let element = document.createElement("span");
      element.textContent = ` > ${text}`;
      title.appendChild(element);

      // Recalcualte levels, Since an element is added
      calculateLevelForElements();
    }
  }
}

backBtn.addEventListener("click", function () {
  let elements = document.querySelectorAll(
    ".nested-header .header-content span"
  );
  elements[elements.length - 1].remove();

  // Recalcualte levels, Since an element is removed
  calculateLevelForElements();

  if (backBtn.style.display == "none") {
    hasChild = false;
  } else {
    hasChild = true;
  }
});

// Calculate level for each header element
function calculateLevelForElements() {
  let elements = document.querySelectorAll(
    ".nested-header .header-content span"
  );
  let index = 0;
  for (let i = elements.length - 1; i >= 0; i--) {
    (elements[index] as any).level = i;
    index++;
  }
}

// Navigate back event handler based on element's level
function navigateBack(event:any) {
  if (event.target && event.target.level) {
    for (let i = 0; i <= event.target.level; i++) {
      backBtn.click();
    }
  }
}

```

{% endtab %}
