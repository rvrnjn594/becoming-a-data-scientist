# Beautiful Soup (Scraping Data from Simple HTML)

Discuss how Beautiful Soup is used to extract data out of the Public Web.

## Beautiful Soup

Have you ever wondered how people extract data out of the public web and analyze it?

They use libraries and other resources that ease the process of extracting the data from the public web (see in more technical terms, "Scraping the Data").

Beautiful Soup is the library that is meant for such purposes.  
The Data Science community has used it for a long time to scrape data from the public web because it pulls data from HTML and XML file.  
It has comprehensive documentation that makes it easy to use.

Web pages are made up of HTML (Hypertext Markup Language).  
Beautiful Soup gets the data straight out of it by specifying the individual elements of HTML.  
 Below is an example of how HTML markup is built and overview of its different tags.

        <!DOCTYPE html>
        <html>
        <head>
            <title>Data Science Course</title>
            <style></style>
        </head>
        <body>
            <h1 class="my-heading"> This is a Heading Tag </h1>
            <p id="my-paragraph"> This is a paragraph in Data Science Course </p>
            <em> This is an emphasis tag in Data Science Course </em>
            <b> This is a tag for Bold Text </b>
            <i> This is a tag for italic text </i>
            <small> This is a tag for small text </small>
            <u> This is a tag for underlined text </u>
            <a href="https://www.educative.io/"> This is a link to Educative Home Page </a>
            <a href="https://www.facebook.com/"> This is a link to Facebook Home Page </a>
            <a href="https://twitter.com/"> This is a link to Twitter Home Page </a>

            <script></script>
        </body>
        </html>

You can see from the snippet above how different tags in HTML are organized.  
We can use these tags to extract relevant things out of them.  
 Beautiful Soup traverses the above tags as specified in the code, to extract the relevant elements.
