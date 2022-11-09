# GroupDocs Annotations API for .NET 
GroupDocs.Annotation for .NET is a set of APIs that allows to expand application capabilities by introducing annotation features for text documents, images, tables, diagrams, presentations, PDFs, and CAD files.

## Features Overview
GroupDocs.Annotation for .NET gives users the possibility to annotate documents without the need to install any additional software. It provides a wide range of annotation types, that can be customized in many different ways. Annotation is usually a comment or a mark attached to a specific part of a document.

Adding comments and notes allows users to efficiently communicate and collaborate within the documents to reach common goals.

### Supported types of annotations
- **Text annotations** (highlighting and commenting, replacing text parts, underlining, and adding strikeouts);
- **Graphic annotations** (highlighting a certain area with a rectangle, adding arrows, measuring the distance between objects, adding notes and comments to any object, creating blackouts, drawing any shapes, etc)
- **Watermark annotations** (horizontal and diagonal watermarks)

### Supported Formats
GroupDocs.Annotation supports 36 document formats including .docx, .rtf, .odt, .xlsx, .pdf, .pptx, .png, .html, and many more. Full list is available here.

### Installation and Development
- GroupDocs.Annotation for .NET can be installed on any 32-bit or 64-bit **operating system** including Microsoft Windows, Linux, and macOS.
- The list of supported **frameworks** includes .NET Standard 2.0, .NET Framework 2.0 or later, .NET Core 2.0 or later, Mono 2.6.7 or later.
- Application development using GroupDocs.Annotation for .NET can be carried out in the following **development environments**: Microsoft Visual Studio 2010 or later, Xamarin.Android, Xamarin.IOS, Xamarin.Mac, MonoDevelop 2.4, and later.

## How to add annotation using GroupDocs.Annotation for .NET

### Adding highlight annotations
Highlighting allows users to color part of the text in the desired color and add comments. That way readers' attention is instantly drawn to specific words, sentences, or paragraphs.

GroupDocs.Annotation for .NET allows customizing the following properties:

- background-color (highlight color)
- font color
- opacity
- points

To add a highlight to the document it is required to:

1. Define input document path using Annotator object
2. Define a place in the document where the highlight should be applied using HighlightAnnotation object
3. Set up highlight properties
4. Call Add method
5. Call Save method

You can use the following code as an example:

```
//Add highlight annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	HighlightAnnotation highlight = new HighlightAnnotation
    {
    	BackgroundColor = 65535,
        CreatedOn = DateTime.Now,
        FontColor = 0,
        Message = "This is highlight annotation",
        Opacity = 0.5,
        PageNumber = 0,
        Points = new List<Point>
        {
        	new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
        },
        Replies = new List<Reply>
        {
        	new Reply
            {
            	Comment = "First comment",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
            	Comment = "Second comment",
                RepliedOn = DateTime.Now
            }
        }
    };
    annotator.Add(highlight);
    annotator.Save("result.pdf");
}

```

### Removing annotation from the document

You can easily remove all previously added annotations and bring the document back to its original state. Removing can be held using one of the following options:
- annotation index
- annotation Object
- list of IDs
- list of annotations

Removing annotations requires completing the following steps:
1. Define input document path using Annotator object
2. Set `AnnotationTypes = AnnotationType.None` using SaveOptions object 
3. Call Save method 

For example, in case of annotation index it can look like this:
```
using (Annotator annotator = new Annotator("result.xlsx"))
{
	annotator.Remove(0);
	annotator.Save("removed.xlsx");
}
```

Using GroupDocs.Annotation for .NET gives you unlimited annotation possibilities, it is user-friendly and simple to use.

You can find more examples of how to use other Annotation types [here](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/tree/master/Examples/GroupDocs.Annotation.Examples.CSharp/BasicUsage/AddAnnotationToTheDocument).
