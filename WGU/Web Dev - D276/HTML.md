Table 2.2.1: Text-formatting elements.

|Element|HTML example|Rendered|Semantics|
|---|---|---|---|
|em|`<em>emphasis</em>`|emphasis|Emphasized text|
|cite|`<cite>cite</cite>`|cite|Title of a work|
|strong|`<strong>strong</strong>`|strong|Important text|
|mark|`<mark>mark</mark>`|mark|Marked or highlighted text|
|var|`<var>variable</var>`|variable|Definition of a variable in a computer program|
|kbd|`<kbd>keyboard</kbd>`|keyboard|Keyboard input|
|code|`<code>code</code>`|code|Computer code|
|samp|`<samp>sample</samp>`|sample|Sample output from a computer|
|b|`<b>bold</b>`|bold|Bold text|
|i|`<i>italic</i>`|italic|Text of an alternate voice or word from another language|
|u|`<u>underline</u>`|underline|Text that is rendered differently from normal text|

#### HTML Containers

Table 3.1.1: Common HTML containers.

| Container | Description                                                                                              |
| --------- | -------------------------------------------------------------------------------------------------------- |
| header    | Container for introductory content                                                                       |
| footer    | Container for content descriptive information about the webpage like author, copyright, or date modified |
| address   | Container for person's or organization's contact information                                             |
| main      | Container for the document's primary content                                                             |
| section   | Container for distinct parts of a document, such as a chapter                                            |
| article   | Container for self-contained content that can be reused independently, such as a news article            |
| nav       | Container for content relating to website navigation                                                     |
| aside     | Container for content not directly related to the main topic of a document                               |
| div       | Generic element for creating block containers                                                            |
| span      | Generic element for creating inline containers                                                           |
|           |                                                                                                          |


### HTML Forms

```HTML
<form action="http://example.com/survey">
  <p>
     <label for="item1">Item 1:</label>
     <input type="checkbox" name="item1" id="item1">
  </p>
  <p>
     <label for="item2">Item 2:</label>
     <input type="checkbox" name="item2" id="item2">
  </p>
  <p>
     <label for="item3">Item 3:</label>
     <input type="checkbox" name="item3" id="item3">
  </p>
  <input type="submit">
</form>
```

By default the HTTP method used if none is provided is GET

#### Input Types
- Checkboxes - type="checkbox"
- Radio - type="radio"
- List 
	- Multiple options can be selected by adding multiple
```HTML
<select name="flagcolors" size="4" multiple>
  <option value="red">Red</option>
  <option value="orange">Orange</option>
  <option value="yellow">Yellow</option>
  <option value="green">Green</option>
  <option value="blue">Blue</option>
  <option value="purple">Purple</option>
  <option value="white">White</option>
  <option value="black">Black</option>
</select>
```
- Dropdown
	- Dropdowns can only have one value and no size attribute
```HTML
<select name="sport">
  <option value="football">Football</option>
  <option value="baseball">Baseball</option>
  <option value="basketball">Basketball</option>
  <option value="hockey">Hockey</option>
  <option value="soccer">Soccer</option>
</select>
```
- Password
- Text
- Datepicker - type="date" min="" max=""
- Colorpicker - type="color" 
- Number - type="number" min="" max=""
- Range - type="range"  min="" max="" value=""
- Combo box
```HTML
<input list="sport">

<datalist id="sport">
   <option value="Baseball">
   <option value="Basketball">
   <option value="Football">
   <option value="Hockey">
   <option value="Soccer">
</datalist>
```
- URL - type="url"
- Tel - type="tel"
- Email - type="email"
- Search - type="search"
- Date Options
	- month - allows selecting month and year
	- week - allows selecting a week and year
	- datetime-local - allows input of date time with no TZ
	- time - allows entering a time


##### Form Validation
| Attribute | Description                                                                 | Example                                                                                              |
| --------- | --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| maxlength | Sets the maximum number of input characters.                                | <!-- Only 4 chars max can be entered --><br>input type="password" maxlength="4"                      |
| minlength | Sets the minimum number of input characters.                                | <!-- At least 5 chars must be entered --><br>input type="password" minlength="5"                     |
| max       | Sets the maximum value that the input can have.                             | <!-- Number may not exceed 212 --><br>input type="number" max="212"                                  |
| min       | Sets the minimum value that the input can have.                             | <!-- May not be earlier than July 4, 1976 --><br>input type="date" min="1976-07-04"                  |
| pattern   | Provides a pattern (called a regular expression) that the input must match. | <!-- Value must be A, B, or C followed by single digit --><br>input type="text" pattern="[ABC][0-9]" |
| required  | States that the input is required and must not be left empty.               | <!-- At least one character must be entered --><br>input type="password" required                    |
| step      | Sets the amount by which the value can change (default is 1).               | <!-- Number is changed by multiples of 5 --><br>input type="range" step="5"                          |

### Audio Video

- audio -plays audio in a webpage
	- source -source element is used to specify an audio file
	- `autoplay` - Boolean attribute that makes the audio begin playing automatically.
	- `controls` - Boolean attribute that displays audio controls for the user to play, pause, and control the volume.
	- `loop` - Boolean attribute that replays the audio upon reaching the end of the audio.
	- `muted` - Boolean attribute that initially mutes the audio.

- video - displays video in a webpage
	- source -source element is used to specify an audio file
	- `autoplay` - Boolean attribute that makes the video begin playing automatically.
	- `controls` - Boolean attribute that displays video controls for the user to play, pause, and control the volume.
	- `loop` - Boolean attribute that replays upon reaching the end of the video.
	- `muted` - Boolean attribute that initially mutes the video.
	- `width` - Specifies the pixel width of the video's display area.

- iframe - allows a webpage to be embedded in a rectangular area of the current webpage.
	- `src` - specifies the URL of the webpage
	- `width` - width
	- `height` - height
