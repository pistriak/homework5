**The Idea**

You need to implement a simple Translation Application that translates any text to Russian. Input parameter should be a path to original text. Possible values are D:/folder/original.txt, https://somedomain.com/original.txt or ftp://ftpdomain.com/original.txt.
To make our life easier let suppose that original text is encoded in UTF-8 encoding.
Application should start in console mode and wait for input. As soon as we've entered a valid path it should translate the original text to Russian and print to console the original and translated texts. In case of error (text could not be obtained by path provided, cannot connect to specified URL, etc.) it should print a message about that error and ask user to enter another path.

**What to do**

1. Application should use Yandex Translate API to translate original texts. More details about the service you can find at http://api.yandex.ru/translate/. To be able to use the service you should get API key and use it in the Application. To do that you should access http://api.yandex.ru/key/form.xml?service=trnsl and follow the instructions. (You will be asked for Authorization. Please, create an account if you do not have it yet). After you obtain the key you should update it in Translator class for YANDEX_API_KEY constant.

2. SourceProvider interface was provided to implement different kind of source, to be able to extract text from different sources.Your target is to make implementation of FileSourceProvider and URLSourceProvider. Both should implement SourceProvider interface. More details about implementation you can find in SourceProvider file.


3. After FileSourceProvider and URLSourceProvider will be implemented you should implement SourceLoader class. Its main purpose is to utilize different implementations of SourceProvider and use corresponding one based on specified path.


4. After that it’s time to complete implementation of Translator class. YANDEX_API_KEY should be already specified if you complete step #1.
Start with String encodeText(String text). This method should take an original text that should be translated and encode it to use as URL parameter.
Then implement String parseContent(String content) method. It shold “extract” translated text from Yandex Translator response. More details about response format you can find at http://api.yandex.ru/translate/doc/dg/reference/translate.xml, we need to use XML interface.
And by using implemented methods and urlSourceProvider you should implement String translate(String original) method that should return translation of original text.


6. Last thing is to put everything together. Some implementation is done in TranslatorController. But you should add right exception handling that was described at the very beginning.

