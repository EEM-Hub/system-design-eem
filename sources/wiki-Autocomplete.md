---
source: https://en.wikipedia.org/wiki/Autocomplete
fetched: 2026-06-19
---

Computing feature predicting ending to a word a user is typing "Word prediction" redirects here. For word prediction in psycholinguistics, see [Prediction in language comprehension](./Prediction_in_language_comprehension). [![](//upload.wikimedia.org/wikipedia/commons/0/09/Autocomplete.png)](./File:Autocomplete.png)Example of the partially typed search term `baby st` being autocompleted to various options 

**Autocomplete**, or **word completion**, is a feature in which an [application](./Application_software) predicts the rest of a word a user is typing. In [Android](./Android_(operating_system)) and [iOS](./IOS)[[1]](./Autocomplete#cite_note-1) [smartphones](./Smartphone), this is called **predictive text**. In [graphical user interfaces](./Graphical_user_interface), users can typically press the [tab key](./Tab_key) to accept a suggestion or the down [arrow key](./Arrow_key) to accept one of several.

 

Autocomplete speeds up [human-computer interactions](./Human-computer_interaction) when it correctly predicts the word a user intends to enter after only a few characters have been typed into a text input field. It works best in domains with a limited number of possible words (such as in [command line interpreters](./Command_line_interpreter)), when some words are much more common (such as when addressing an [e-mail](./E-mail)), or writing structured and predictable text (as in [source code editors](./Source_code_editor)).

 

Many autocomplete [algorithms](./Algorithm) learn new words after the user has written them a few times, and can suggest alternatives based on the learned habits of the individual user.

 

## Definition

 

### Original purpose

 

The original purpose of word prediction software was to help people with [physical disabilities](./Physical_disabilities) increase their typing speed,[[2]](./Autocomplete#cite_note-tam2009-2) as well as to help them decrease the number of keystrokes needed in order to complete a word or a sentence.[[3]](./Autocomplete#cite_note-anson-3) The need to increase speed is noted by the fact that people who use [speech-generating devices](./Speech-generating_device) generally produce speech at a rate that is less than 10% as fast as people who use oral speech.[[4]](./Autocomplete#cite_note-trnka-4) But the function is also very useful for anybody who writes text, particularly people–such as medical doctors–who frequently use long, hard-to-spell terminology that may be technical or medical in nature.

 

### Description

 

Autocomplete or word completion works so that when the writer writes the first letter or letters of a word, the program predicts one or more possible words as choices. If the intended word is included in the list, the writer can select it, for example, by using the number keys. If the word that the user wants is not predicted, the writer must enter the next letter of the word. At this time, the word choice(s) is altered so that the words provided begin with the same letters as those that have been selected. When the word that the user wants appears it is selected, and the word is inserted into the text.[[5]](./Autocomplete#cite_note-b77-5)[[6]](./Autocomplete#cite_note-witten-6) In another form of word prediction, words most likely to follow the just written one are predicted, based on recent word pairs used.[[6]](./Autocomplete#cite_note-witten-6)  Word prediction uses [language modeling](./Language_modeling), where within a set vocabulary the words are most likely to occur are calculated.[[7]](./Autocomplete#cite_note-7)  Along with language modeling, basic word prediction on [AAC](./Augmentative_and_alternative_communication) devices is often coupled with a [frecency](./Frecency) model, where words the AAC user has used recently and frequently are more likely to be predicted.[[4]](./Autocomplete#cite_note-trnka-4)  Word prediction software often also allows the user to enter their own words into the word prediction dictionaries either directly, or by "learning" words that have been written.[[5]](./Autocomplete#cite_note-b77-5)[[6]](./Autocomplete#cite_note-witten-6) Some search returns related to genitals or other vulgar terms are often omitted from autocompletion technologies, as are morbid terms[[8]](./Autocomplete#cite_note-8)[[9]](./Autocomplete#cite_note-9)

 

## History

 

The autocomplete and predictive text technology was invented by Chinese scientists and linguists in the 1950s to solve the input inefficiency of the [Chinese typewriter](./Chinese_typewriter),[[10]](./Autocomplete#cite_note-10) as the typing process involved finding and selecting thousands of [logographic characters](./Chinese_characters) on a tray,[[11]](./Autocomplete#cite_note-Sorrel2009-11) drastically slowing down the word processing speed.[[12]](./Autocomplete#cite_note-12)[[13]](./Autocomplete#cite_note-13)

 

In the 1950s, typists came to rearrange the character layout from the standard dictionary layout to groups of common words and phrases.[[14]](./Autocomplete#cite_note-Mullaney2018-14) Chinese typewriter engineers innovated mechanisms to access common characters accessible at the fastest speed possible by [word prediction](./Word_prediction), a technique used today in [Chinese input methods for computers](./Chinese_input_methods_for_computers), and in text messaging in many languages. According to [Stanford University](./Stanford_University) historian Thomas Mullaney, the development of modern Chinese typewriters from the 1960s to 1970s influenced the development of modern computer word processors and affected the development of computers themselves.[[15]](./Autocomplete#cite_note-Stanford2010-15)[[11]](./Autocomplete#cite_note-Sorrel2009-11)[[14]](./Autocomplete#cite_note-Mullaney2018-14)

 

## Types of autocomplete tools

 

There are standalone tools that add autocomplete functionality to existing applications. These programs monitor user keystrokes and suggest a list of words based on first typed letter(s). Examples are Typingaid and Letmetype.[[16]](./Autocomplete#cite_note-16)[[17]](./Autocomplete#cite_note-17) LetMeType, freeware, is no longer developed. The author has published the source code and allows anybody to continue development. TypingAid, also freeware, is actively developed. IntelliComplete, available as both freeware and payware, works only in certain programs which hook into the IntelliComplete server program.[[18]](./Autocomplete#cite_note-18) The first autocomplete software was Smartype, which dates back to the late 1980s and is still available today.  It was initially developed for medical transcriptionists working in WordPerfect for MS/DOS, but it now functions for any application in any Windows or Web-based program.

 

### Autocorrection

 

[Autocorrection](./Autocorrection) is a related feature that involves automatic replacement of a particular string with another one, usually one that is longer and harder to type, such as "myname" with "Lee John Nikolai François Al Rahman". This can also quietly fix simple typing errors, such as turning "[teh](./Teh)" into "the". Several autocomplete programs, standalone or integrated in text editors, based on word lists, also include a shorthand function for often-used phrases.[*[citation needed](./Wikipedia:Citation_needed)*]

 

### Context completion

 

**Context completion** is a [text editor](./Text_editor) feature, similar to word completion, which completes words (or entire phrases) based on the current context and context of other similar words within the same document, or within some training data set. The main advantage of context completion is the ability to predict anticipated words more precisely and even with no initial letters. The main disadvantage is the need of a training data set, which is typically larger for context completion than for simpler word completion. Most common use of context completion is seen in advanced programming language editors and [IDEs](./Integrated_development_environment), where training data set is inherently available and context completion makes more sense to the user than broad word completion would.[*[citation needed](./Wikipedia:Citation_needed)*]

 

**Line completion** is a type of context completion, first introduced by Juraj Simlovic in [TED Notepad](./TED_Notepad) in July 2006. The context in line completion is the current line while the current document poses as a training dataset. When the user begins a line that starts with a frequently-used phrase, the editor automatically completes it up to the position where similar lines differ or proposes a list of common continuations.[*[citation needed](./Wikipedia:Citation_needed)*]

 

## Software integration

 

### In web browsers

 [![](//upload.wikimedia.org/wikipedia/commons/1/15/Autocomplete_Mozilla_Firefox_23_-_Wikipedia_de_search.png)](./File:Autocomplete_Mozilla_Firefox_23_-_Wikipedia_de_search.png)Autocomplete of the search box in [Mozilla Firefox](./Mozilla_Firefox) 

In [web browsers](./Web_browser), autocomplete is done in the [address bar](./Address_bar) (using items from the browser's history) and in text boxes on frequently used pages, such as a [search engine](./Search_engine)'s search box. Autocomplete for web addresses is particularly convenient because the full addresses are often long and difficult to type correctly. 

 

#### In web forms

 

Autocompletion or "autofill" is frequently found in web browsers, used to fill in [web forms](./Form_(HTML)) automatically. When a user inputs data into a form and subsequently submits it, the web browser will often save the form's contents by default.[*[citation needed](./Wikipedia:Citation_needed)*]

 

This feature is commonly used to fill in login credentials. However, when a password field is detected, the web browser will typically ask the user for explicit confirmation before saving the password in its password store, often secured with a built-in [password manager](./Password_manager) to allow the use of a "master password" before credentials can be autofilled.[[19]](./Autocomplete#cite_note-19)

 

Most of the time, such as in Internet Explorer and [Google Toolbar](./Google_Toolbar), the entries depend on the form field's name, so as to not enter street names in a last name field or vice versa. For this use, proposed names for such form fields, in earlier HTML 5 specifications this RFC is no longer referenced, thus leaving the selection of names up to each browser's implementation.

 

Certain web browsers such as [Opera](./Opera_(web_browser)) automatically autofill [credit card](./Credit_card) information and [addresses](./Street_address).[[20]](./Autocomplete#cite_note-20)

 

An individual webpage may enable or disable browser autofill by default. This is done in [HTML](./HTML) with the `autocomplete` attribute in a `<form>` element or its corresponding form elements.

 
```
<!-- Autocomplete turned on by default -->
<form autocomplete="on">

  <!-- This form element has autocomplete turned on -->
  <input name="username" autocomplete="on">

  <!-- While this one inherits its parent form's value -->
  <input name="password" type="password">
</form>

```
 

It has been shown that the autofill feature of modern browsers can be exploited in a [phishing](./Phishing) attack with the use of hidden form fields, which allows [personal information](./Personal_information) such as the user's phone number to be collected.[[21]](./Autocomplete#cite_note-21)

 

HTML has a `datalist` element that can be used to feed an input element with autocompletions.[[22]](./Autocomplete#cite_note-22)

 
```
<label for="ice-cream-choice">Choose a flavor:</label>
<input list="ice-cream-flavors" id="ice-cream-choice" name="ice-cream-choice" />

<datalist id="ice-cream-flavors">
  <option value="Chocolate"></option>
  <option value="Coconut"></option>
  <option value="Mint"></option>
  <option value="Strawberry"></option>
  <option value="Vanilla"></option>
</datalist>

```
 

### In e-mail programs

 

In [e-mail programs](./E-mail_program) autocomplete is typically used to fill in the e-mail addresses of the intended recipients. Generally, there are a small number of frequently-used e-mail addresses, hence it is relatively easy to use autocomplete to select among them. Like web addresses, e-mail addresses are often long, making typing them completely inconvenient.[*[citation needed](./Wikipedia:Citation_needed)*]

 

For instance, Microsoft [Outlook Express](./Outlook_Express) will find addresses based on the name that is used in the address book.  [Google](./Google)'s [Gmail](./Gmail) will find addresses by any string that occurs in the address or stored name.[*[citation needed](./Wikipedia:Citation_needed)*]

 

### In retail and e-commerce websites

 

Autocomplete, often called predictive search, is used to suggest relevant products, categories, or queries as a shopper types into the search bar. This feature helps reduce typing effort and guides users toward popular or high-converting search terms. Many e-commerce systems generate these suggestions dynamically, based on recent search data or trending products, to improve both speed and discoverability.[[23]](./Autocomplete#cite_note-23)

 

### In search engines

 

In search engines, autocomplete user interface features provide users with suggested queries or results as they type their query in the search box.  This is also commonly called *autosuggest* or *[incremental search](./Incremental_search)*.  This type of search often relies on matching algorithms that forgive entry errors such as phonetic [Soundex](./Soundex) algorithms or the language independent [Levenshtein algorithm](./Levenshtein_algorithm).  The challenge remains to search large indices or popular query lists in under a few milliseconds so that the user sees results pop up while typing.

 

Autocomplete can have an adverse effect on individuals and businesses when negative search terms are suggested when a search takes place. Autocomplete has now become a part of [reputation management](./Reputation_management) as companies linked to negative search terms such as scam, complaints and fraud seek to alter the results. Google in particular have listed some of the aspects that affect how their algorithm works, but this is an area that is open to manipulation.[[24]](./Autocomplete#cite_note-24)

 

### In source code editors

 Main article: [Code completion](./Code_completion) [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/28/Qt_Creator_5.0-Autocomplete.png/250px-Qt_Creator_5.0-Autocomplete.png)](./File:Qt_Creator_5.0-Autocomplete.png)Code completion in [Qt Creator](./Qt_Creator) 5.0: The programmer types some code, and when the software detects a recognizable string such as a variable identifier or class name it presents a menu to the programmer which contains the complete name of the identified variable or the methods applicable to the detected class, and the programmer makes a choice with her or his mouse or with the keyboard arrow keys. If the programmer continues typing without making a choice, then the menu disappears. 

Autocompletion of source code is also known as **code completion**. In a [source code editor](./Source_code_editor), autocomplete is greatly simplified by the regular structure of the [programming language](./Programming_language). There are usually only a limited number of words meaningful in the current context or [namespace](./Namespace), such as names of variables and functions. An example of code completion is [Microsoft](./Microsoft)'s [IntelliSense](./IntelliSense) design. It involves showing a pop-up list of possible completions for the current input prefix to allow the user to choose the right one. This is particularly useful in [object-oriented programming](./Object-oriented_programming) because often the programmer will not know exactly what [members](./Member_variable) a particular [class](./Class_(computer_science)) has. Therefore, autocomplete then serves as a form of convenient [documentation](./Software_documentation#Technical_documentation) as well as an input method.

 

Another beneficial feature of autocomplete for source code is that it encourages the programmer to use longer, more descriptive variable names, hence making the [source code](./Source_code) more readable. Typing large words which may contain [camel case](./Camel_case) like `numberOfWordsPerParagraph` can be difficult, but autocomplete allows a programmer to complete typing the word using a fraction of the keystrokes.

 

### In database query tools

 

Autocompletion in [database query](./Database_query) tools allows the user to autocomplete the table names in an [SQL](./SQL) statement and column names of the tables referenced in the SQL statement. As text is typed into the [editor](./Source_code_editor), the context of the cursor within the SQL statement provides an indication of whether the user needs a table completion or a table column completion.  The table completion provides a list of tables available in the [database server](./Database_server) the user is connected to. The column completion provides a list of columns for only tables referenced in the SQL statement. [SQL Server Management Studio](./SQL_Server_Management_Studio) provides autocomplete in query tools.[*[citation needed](./Wikipedia:Citation_needed)*]

 

### In word processors

 

In many [word processing](./Word_processing) programs, autocompletion decreases the amount of time spent typing repetitive words and phrases. The source material for autocompletion is either gathered from the rest of the current document or from a list of common words defined by the user. Currently [Apache OpenOffice](./Apache_OpenOffice), [Calligra Suite](./Calligra_Suite), [KOffice](./KOffice), [LibreOffice](./LibreOffice) and [Microsoft Office](./Microsoft_Office) include support for this kind of autocompletion, as do advanced text editors such as [Emacs](./Emacs) and [Vim](./Vim_(text_editor)).

 
- [Apache OpenOffice Writer](./Apache_OpenOffice_Writer) and [LibreOffice Writer](./LibreOffice_Writer) have a working word completion program that proposes words previously typed in the text, rather than from the whole dictionary
- [Microsoft Excel](./Microsoft_Excel) spreadsheet application has a working word completion program that proposes words previously typed in upper cells

 

### In command-line interpreters

 Main article: [Command-line completion](./Command-line_completion) [![](//upload.wikimedia.org/wikipedia/commons/4/4f/Powershell_Intellisense_example_for_the_Get-Process_cmdlet.gif)](./File:Powershell_Intellisense_example_for_the_Get-Process_cmdlet.gif)Command-line completion in [PowerShell](./PowerShell) 

In a [command-line interpreter](./Command-line_interpreter), such as [Unix](./Unix)'s [sh](./Bourne_shell) or [bash](./Bash_(Unix_shell)), or [Windows](./Microsoft_Windows)'s [cmd.exe](./Cmd.exe) or [PowerShell](./PowerShell), or in similar [command line interfaces](./Command_line_interface), autocomplete of command names and file names may be accomplished by keeping track of all the possible names of things the user may access. Here autocomplete is usually done by pressing the [Tab ↹](./Tab_key) key after typing the first several letters of the word. For example, if the only file in the current directory that starts with x is xLongFileName, the user may prefer to type x and autocomplete to the complete name. If there were another file name or command starting with x in the same scope, the user would type more letters or press the Tab key repeatedly to select the appropriate text.

 

## Efficiency

 

### Research

 

Although research has shown that word prediction software does decrease the number of keystrokes needed and improves the written productivity of children with disabilities,[[2]](./Autocomplete#cite_note-tam2009-2) there are mixed results as to whether or not word prediction actually increases speed of output.[[25]](./Autocomplete#cite_note-25)[[26]](./Autocomplete#cite_note-26)  It is thought that the reason why word prediction does not always increase the rate of text entry is because of the increased [cognitive load](./Cognitive_load) and requirement to move eye gaze from the keyboard to the monitor.[[2]](./Autocomplete#cite_note-tam2009-2)

 

In order to reduce this cognitive load, parameters such as reducing the list to five likely words, and having a vertical layout of those words may be used.[[2]](./Autocomplete#cite_note-tam2009-2)  The vertical layout is meant to keep head and eye movements to a minimum, and also gives additional visual cues because the word length becomes apparent.[[27]](./Autocomplete#cite_note-27)  Although many software developers believe that if the word prediction list follows the [cursor](./Cursor_(computers)), that this will reduce eye movements,[[2]](./Autocomplete#cite_note-tam2009-2) in a study of children with [spina bifida](./Spina_bifida) by Tam, Reid, O'Keefe & Nauman (2002) it was shown that typing was more accurate, and that the children also preferred when the list appeared at the bottom edge of the screen, at the midline. Several studies have found that word prediction performance and satisfaction increases when the word list is closer to the keyboard, because of the decreased amount of eye-movements needed.[[28]](./Autocomplete#cite_note-28)

 

Software with word prediction is produced by multiple manufacturers. The software can be bought as an add-on to common programs such as [Microsoft Word](./Microsoft_Word) (for example, [WordQ+SpeakQ](./WordQ+SpeakQ), Typing Assistant,[[29]](./Autocomplete#cite_note-29) Co:Writer,[*[citation needed](./Wikipedia:Citation_needed)*] Wivik,[*[citation needed](./Wikipedia:Citation_needed)*] Ghotit Dyslexia),[*[citation needed](./Wikipedia:Citation_needed)*] or as one of many features on an AAC device (PRC's Pathfinder,[*[citation needed](./Wikipedia:Citation_needed)*] Dynavox Systems,[*[citation needed](./Wikipedia:Citation_needed)*] Saltillo's ChatPC products[*[citation needed](./Wikipedia:Citation_needed)*]). Some well known programs: Intellicomplete,[*[citation needed](./Wikipedia:Citation_needed)*] which is available in both a freeware and a payware version, but works only with programs which are made to work with it. Letmetype[*[citation needed](./Wikipedia:Citation_needed)*] and Typingaid[*[citation needed](./Wikipedia:Citation_needed)*] are both freeware programs which work in any text editor.

 

An early version of autocompletion was described in 1967 by [H. Christopher Longuet-Higgins](./H._Christopher_Longuet-Higgins) in his Computer-Assisted Typewriter (CAT),[[30]](./Autocomplete#cite_note-30) "such words as 'BEGIN' or 'PROCEDURE' or identifiers introduced by the programmer, would be automatically completed by the CAT after the programmer had typed only one or two symbols."

 

## See also

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Software autocompletion](https://commons.wikimedia.org/wiki/Category:Software%20autocompletion).  
- [Autocorrection](./Autocorrection) – Feature on word processors to automatically correct misspelled words, automatic correction of misspelled words.
- [Autofill](./Autofill) – Computing feature predicting ending to a word a user is typingPages displaying short descriptions of redirect targets
- [Combo box](./Combo_box) – User interface element
- [Context-sensitive user interface](./Context-sensitive_user_interface) – Concept in human-computer interaction
- [GitHub Copilot](./GitHub_Copilot) – Artificial intelligence tool
- [Google Feud](./Google_Feud) – Website game
- [Incremental search](./Incremental_search) – User interface method to search for text
- [OpenSearch (specification)](./OpenSearch_(specification)) – Protocols for syndicating search results
- [Predictive text](./Predictive_text) – Input technology for mobile phone keypads
- [Qwerty effect](./Qwerty_effect) – Effects of computer keyboard layout on language and behavior
- [Search suggest drop-down list](./Search_suggest_drop-down_list) – Query feature used in computing
- [Snippet](./Snippet_(programming)) – Small amount of source code used for productivity

 

## References

 
1. [↑](./Autocomplete#cite_ref-1) ["How to use Auto-Correction and predictive text on your iPhone, iPad, or iPod touch"](https://support.apple.com/en-us/HT207525). *Apple Support*. Apple.
2. [1](./Autocomplete#cite_ref-tam2009_2-0) [2](./Autocomplete#cite_ref-tam2009_2-1) [3](./Autocomplete#cite_ref-tam2009_2-2) [4](./Autocomplete#cite_ref-tam2009_2-3) [5](./Autocomplete#cite_ref-tam2009_2-4) Tam, Cynthia; Wells, David (2009). "Evaluating the Benefits of Displaying Word Prediction Lists on a Personal Digital Assistant at the Keyboard Level". *Assistive Technology*. **21** (3): 105–114. [doi](./Doi_(identifier)):[10.1080/10400430903175473](https://doi.org/10.1080%2F10400430903175473). [PMID](./PMID_(identifier)) [19908678](https://pubmed.ncbi.nlm.nih.gov/19908678). [S2CID](./S2CID_(identifier)) [23183632](https://api.semanticscholar.org/CorpusID:23183632).
3. [↑](./Autocomplete#cite_ref-anson_3-0) Anson, D.; Moist, P.; Przywara, M.; Wells, H.; Saylor, H.; Maxime, H. (2006). ["The Effects of Word Completion and Word Prediction on Typing Rates Using On-Screen Keyboards"](https://www.researchgate.net/publication/6567291). *Assistive Technology*. **18** (2): 146–154. [doi](./Doi_(identifier)):[10.1080/10400435.2006.10131913](https://doi.org/10.1080%2F10400435.2006.10131913). [PMID](./PMID_(identifier)) [17236473](https://pubmed.ncbi.nlm.nih.gov/17236473). [S2CID](./S2CID_(identifier)) [11193172](https://api.semanticscholar.org/CorpusID:11193172).
4. [1](./Autocomplete#cite_ref-trnka_4-0) [2](./Autocomplete#cite_ref-trnka_4-1) Trnka, K.; Yarrington, J.M.; McCoy, K.F. (2007). "The Effects of Word Prediction on Communication Rate for AAC". *NAACL-Short '07: Human Language Technologies 2007: The Conference of the North American Chapter of the Association for Computational Linguistics*. Vol. Companion Volume, Short Papers. Association for Computational Linguistics. pp. 173–6. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.363.2416](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.363.2416).
5. [1](./Autocomplete#cite_ref-b77_5-0) [2](./Autocomplete#cite_ref-b77_5-1) Beukelman, D.R.; Mirenda, P. (2005). *Augmentative and Alternative Communication: Supporting Children and Adults with Complex Communication Needs* (3rd ed.). Baltimore, MD: Brookes. p. 77. [ISBN](./ISBN_(identifier)) [9781557666840](./Special:BookSources/9781557666840). [OCLC](./OCLC_(identifier)) [254228982](https://search.worldcat.org/oclc/254228982).
6. [1](./Autocomplete#cite_ref-witten_6-0) [2](./Autocomplete#cite_ref-witten_6-1) [3](./Autocomplete#cite_ref-witten_6-2) Witten, I.H.; Darragh, John J. (1992). [*The reactive keyboard*](https://books.google.com/books?id=obxCY0wcaTgC&pg=PA44). Cambridge University Press. pp. 43–44. [ISBN](./ISBN_(identifier)) [978-0-521-40375-7](./Special:BookSources/978-0-521-40375-7).
7. [↑](./Autocomplete#cite_ref-7) Jelinek, F. (1990). ["Self-Organized Language Modeling for Speech Recognition"](https://books.google.com/books?id=iDHgboYRzmgC&pg=PA450). In Waibel, A.; Lee, Kai-Fu (eds.). *Readings in Speech Recognition*. Morgan Kaufmann. p. 450. [ISBN](./ISBN_(identifier)) [9781558601246](./Special:BookSources/9781558601246).
8. [↑](./Autocomplete#cite_ref-8) Oster, Jan (2015). "Communication, defamation and liability of intermediaries". *Legal Studies*. **35** (2): 348–368. [doi](./Doi_(identifier)):[10.1111/lest.12064](https://doi.org/10.1111%2Flest.12064). [S2CID](./S2CID_(identifier)) [143005665](https://api.semanticscholar.org/CorpusID:143005665).
9. [↑](./Autocomplete#cite_ref-9) McCulloch, Gretchen (11 February 2019). ["Autocomplete Presents the Best Version of You"](https://www.wired.com/story/autocomplete-presents-the-best-version-of-you). *[Wired](./Wired_(magazine))*. Retrieved 11 February 2019.
10. [↑](./Autocomplete#cite_ref-10) Mcclure, Max (12 November 2012). ["Chinese typewriter anticipated predictive text, finds historian"](https://phys.org/news/2012-11-chinese-typewriter-text-historian.html).
11. [1](./Autocomplete#cite_ref-Sorrel2009_11-0) [2](./Autocomplete#cite_ref-Sorrel2009_11-1) Sorrel, Charlie (February 23, 2009). ["How it Works: The Chinese Typewriter"](https://www.wired.com/gadgetlab/2009/02/how-it-works-ch/). *[Wired](./Wired_(magazine))*.
12. [↑](./Autocomplete#cite_ref-12) Greenwood, Veronique (14 December 2016). ["Why predictive text is making you forget how to write"](https://www.newscientist.com/article/mg23231041-000-typecast/). *New Scientist*.
13. [↑](./Autocomplete#cite_ref-13) O'Donovan, Caroline (16 August 2016). ["How This Decades-Old Technology Ushered In Predictive Text"](https://www.buzzfeednews.com/article/carolineodonovan/how-this-decades-old-technology-ushered-in-predictive-text). *Buzzfeed*.
14. [1](./Autocomplete#cite_ref-Mullaney2018_14-0) [2](./Autocomplete#cite_ref-Mullaney2018_14-1) Mullaney, Thomas S. (2018-07-16). ["90,000 Characters on 1 Keyboard"](https://foreignpolicy.com/2018/07/16/1-billion-people-100000-characters-1-typewriter-chinese/). *Foreign Policy*. Retrieved 25 April 2020.
15. [↑](./Autocomplete#cite_ref-Stanford2010_15-0) [*Featured Research – world's first history of the Chinese typewriter*](https://shc.stanford.edu/stanford-humanities-center/news/featured-research-worlds-first-history-chinese-typewriter), Humanities at Stanford, January 2, 2010
16. [↑](./Autocomplete#cite_ref-16) ["[AHK 1.1]TypingAid v2.22.0 — Word AutoCompletion Utility"](https://www.autohotkey.com/board/topic/49517-ahk-11typingaid-v2220-word-autocompletion-utility/). AutoHotkey. 2010.
17. [↑](./Autocomplete#cite_ref-17) Clasohm, Carsten (2011). ["LetMeType"](https://web.archive.org/web/20120527195205/http://www.clasohm.com/lmt/en/). Archived from [the original](http://www.clasohm.com/lmt/en/) on 2012-05-27. Retrieved 2012-05-09.
18. [↑](./Autocomplete#cite_ref-18) ["Medical Transcription Software — IntelliComplete"](http://www.intellicomplete.com/). FlashPeak. 2014.
19. [↑](./Autocomplete#cite_ref-19) ["Password Manager - Remember, delete and edit logins and passwords in Firefox"](https://support.mozilla.org/en-US/kb/password-manager-remember-delete-edit-logins). *Firefox Support*.
20. [↑](./Autocomplete#cite_ref-20) ["Autofill: What web devs should know, but don't"](https://cloudfour.com/thinks/autofill-what-web-devs-should-know-but-dont/). *Cloud Four*. 19 May 2016.
21. [↑](./Autocomplete#cite_ref-21) ["Browser Autofill Profiles Can Be Abused for Phishing Attacks"](https://www.bleepingcomputer.com/news/security/browser-autofill-profiles-can-be-abused-for-phishing-attacks/). *Bleeping Computer*.
22. [↑](./Autocomplete#cite_ref-22) [": The HTML Data List element - HTML | MDN"](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/datalist). *developer.mozilla.org*. 9 July 2025. Retrieved 21 July 2025.
23. [↑](./Autocomplete#cite_ref-23) Hearst, Marti A. (2009). *Search user interfaces*. New York, NY: Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-0-521-11379-3](./Special:BookSources/978-0-521-11379-3).
24. [↑](./Autocomplete#cite_ref-24) Davids, Neil (2015-06-03). ["Changing Autocomplete Search Suggestions"](https://rankstar.io/autosuggest-creation-services/). *Reputation Station*. Retrieved 19 June 2015.
25. [↑](./Autocomplete#cite_ref-25) Dabbagh, H.H.; Damper, R.I. (1985). "Average Selection Length and Time as Predictors of Communication Rate". In Brubaker, C.; Hobson, D.A. (eds.). *Technology, a Bridge to Independence: Proceedings of the Eighth Annual Conference on Rehabilitation Technology, Memphis, Tennessee, June 24–28th, 1985*. Rehabilitation Engineering Society of North America. pp. 404–6. [OCLC](./OCLC_(identifier)) [15055289](https://search.worldcat.org/oclc/15055289). 80177b42-e668-4ed5-a256-49b9440bdfa5.
26. [↑](./Autocomplete#cite_ref-26) Goodenough-Trepagnier, C.; Rosen, M.J. (1988). "Predictive Assessment for Communication Aid Prescription: Motor-Determined Maximum Communication Rate". In Bernstein, L.E. (ed.). *The vocally impaired: Clinical Practice and Research*. Philadelphia: Grune & Stratton. pp. 165–185. [ISBN](./ISBN_(identifier)) [9780808919087](./Special:BookSources/9780808919087). [OCLC](./OCLC_(identifier)) [567938402](https://search.worldcat.org/oclc/567938402). as cited in [Tam & Wells 2009](./Autocomplete#CITEREFTamWells2009)
27. [↑](./Autocomplete#cite_ref-27) Swiffin, A.L.; Arnott, J.L.; Pickering, J.A.; Newell, A.F. (1987). "Adaptive and predictive techniques in a communication prosthesis". *Augmentative and Alternative Communication*. **3** (4): 181–191. [doi](./Doi_(identifier)):[10.1080/07434618712331274499](https://doi.org/10.1080%2F07434618712331274499). as cited in [Tam & Wells 2009](./Autocomplete#CITEREFTamWells2009)
28. [↑](./Autocomplete#cite_ref-28) Tam, C.; Reid, D.; Naumann, S.; O'Keefe, B. (2002). ["Perceived benefits of word prediction intervention on written productivity in children with spina bifida and hydrocephalus"](https://doi.org/10.1002%2Foti.167). *Occupational Therapy International*. **9** (3): 237–255. [doi](./Doi_(identifier)):[10.1002/oti.167](https://doi.org/10.1002%2Foti.167). [PMID](./PMID_(identifier)) [12374999](https://pubmed.ncbi.nlm.nih.gov/12374999). as cited in [Tam & Wells 2009](./Autocomplete#CITEREFTamWells2009).
29. [↑](./Autocomplete#cite_ref-29) Sumit Software (2010). ["Typing Assistant – New generation of word prediction software"](https://www.prlog.org/10519217-typing-assistant-new-generation-of-word-prediction-software.html). PRLog: Press Release Distribution.
30. [↑](./Autocomplete#cite_ref-30) Longuet-Higgins, H.C.; Ortony, A. (1968). ["The Adaptive Memorization of Sequences"](https://archive.org/details/mi3_20200519/page/310/mode/2up). *Machine Intelligence 3, Proceedings of the Third Annual Machine Intelligence Workshop, University of Edinburgh, September 1967*. Edinburgh University Press. pp. 311–322.

 

## External links

   [![Wiktionary logo](//upload.wikimedia.org/wikipedia/commons/thumb/9/99/Wiktionary-logo-en-v2.svg/40px-Wiktionary-logo-en-v2.svg.png)](./File:Wiktionary-logo-en-v2.svg) Look up ***[autocomplete](https://en.wiktionary.org/wiki/Special:Search/autocomplete)*** in Wiktionary, the free dictionary.  
- [Live Search Explained](http://justaddwater.dk/2006/01/26/live-search-explained/)—Examples and explanations of working web examples plus a discussion of the usability benefits compared to traditional search.
- [Google Feud](http://www.googlefeud.com/)—The first and most popular of many games built using autocomplete data, which won a [Webby Award](./Webby_Award) for "Best Game" in 2016.
- [Mimicking Google's Search Autocomplete With a Single MigratoryData Server](http://highscalability.com/blog/2016/12/13/a-scalable-alternative-to-restful-communication-mimicking-go.html/)—Optimize search autocomplete using persistent [WebSocket](./WebSocket) connections to achieve both low-latency search experience and bandwidth improvement.