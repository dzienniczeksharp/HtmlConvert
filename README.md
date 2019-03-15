# HtmlConvert
HtmlConvert is a very small and simple c# library that provides annotation based HTML -> .NET object converter.
Inspired by `JSON.NET` and `jspoon`, based on `HtmlAgilityPack` and `Hazz`

Sample use
```csharp
            var testObject = HtmlConvert.DeserializeObject<TestObject>(@"
  <html>
      <head></head>
      <body>
        <div>
            <p class='title'>HtmlConvert</p>
            <p>HTML to .NET object converter</p>
        </div>
        <p class='number'>3</p>
        <p class='bool'>false</p>
      </body>
  </html>");

            // testObject.Title = "HtmlConvert"
            // testObject.Description = "HTML to .NET object converter"
            // testObject.Number = "3"
            // testObject.Bool = false
        }

        class TestObject
        {
            [HtmlProperty(".title")]
            public string Title { get; set; }

            [HtmlProperty("html body div p:last-child")]
            public string Description { get; set; }

            [HtmlProperty(".number")]
            public int Number { get; set; }

            [HtmlProperty(".bool")]
            public bool Bool { get; set; }
        }
```