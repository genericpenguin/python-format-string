# Python Format String Visualizer

A single-page web application for visualizing and understanding Python string formatting syntax. Similar to tools like Rubular for regex or Pythex for Python regex, this tool helps you learn and debug Python format strings and f-strings by breaking them down into their component parts with color-coded explanations. I was working through the "Effective Python" book by Brett Slatkin and wanted to have an easier way to understand the f-string syntax. Written by Claude because who has time.

## What It Does

The Python Format String Visualizer parses Python format strings and f-strings, displaying each element with:

- **Color-coded tokens** - Each part of the format string gets a unique color based on its function
- **Clear explanations** - Human-readable descriptions of what each component does
- **Visual grouping** - Related elements are grouped together for easier understanding

## Features

### Supported Input Formats

1. **Format Specification Only**
   ```
   :>30
   :.2f
   :*^30,.2f
   ```

2. **Replacement Fields**
   ```
   {value:.2f}
   {key:<10}
   {price:,.2f}
   ```

3. **Complete F-Strings**
   ```
   f'{key:<10} = {value:.2f}'
   f'{price:,.2f}'
   f'{name!r:>20}'
   ```

### Live Preview with Pyodide

The app includes a **Live Preview** feature powered by [Pyodide](https://pyodide.org/) (Python running in the browser):

- **Automatic variable detection** - Extracts variables from your format string
- **Type selection** - Choose the data type for each variable (string, int, float, list, dict, bool)
- **Smart defaults** - Pre-populates sensible example values based on variable names
- **Real Python execution** - Uses actual Python to format your string, ensuring 100% accuracy
- **Error display** - Shows Python errors clearly when formatting fails

The Live Preview section appears automatically when you parse a format string with variables. Simply provide values for each variable and click "Format" to see the result.

### Visual Elements

The app uses distinct colors for each formatting component:

- **Variable names** - Purple/Blue background
- **Conversion flags** (!r, !s, !a) - Pink background
- **Fill characters** - Yellow background
- **Alignment** (<, >, ^, =) - Teal background
- **Sign** (+, -, space) - Purple background
- **Alternate form** (#) - Orange background
- **Zero padding** (0) - Red background
- **Width** - Green background
- **Grouping** (,, _) - Rose background
- **Precision** (.2, .5, etc.) - Blue background
- **Type specifiers** (f, d, x, etc.) - Purple background

## Usage

1. Open `index.html` in your web browser
2. Enter a format string in the input text area (or click an example button)
3. The visualization updates automatically after 1 second of inactivity
4. View the color-coded breakdown and explanations
5. If your format string has variables, use the Live Preview section to:
   - Select the data type for each variable
   - Enter example values
   - Click "Format" to see the actual Python-formatted output

## Examples

The app includes built-in examples:

- **Example 1**: `:>30` - Right alignment with width
- **Example 2**: `:.2f` - Precision formatting for floats
- **Example 3**: `f'{key:<10} = {value:.2f}'` - Complete f-string with multiple fields
- **Example 4**: `{:*^30,.2f}` - Complex formatting with fill, alignment, width, grouping, and precision

## Reference Documentation

For complete details on Python's format string syntax, see the included [f-string-format.txt](f-string-format.txt) file, which contains the official Python documentation for:

- Format String Syntax
- Format Specification Mini-Language
- Replacement field grammar
- All available format specifiers and their meanings

## Technical Details

- **Pure vanilla JavaScript** - No build process or compilation required
- **Tailwind CSS** - Loaded from CDN
- **Pyodide** - Python 3.11 running in WebAssembly for live preview (~6-8MB, loaded on-demand)
- **Single HTML file** - Easy to deploy and share
- **Works offline** - After initial load (including Pyodide cache)

## Browser Compatibility

Works in all modern browsers that support ES6 JavaScript:
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)

## How It Works

The parser uses regular expressions and character-by-character parsing to:

1. Detect the input format (format spec, replacement field, or f-string)
2. Extract literal text from replacement fields in f-strings
3. Parse replacement fields into variable name, conversion, and format spec
4. Break down format specifications into their components following Python's grammar:
   - `[[fill]align][sign][z][#][0][width][grouping][.precision[grouping]][type]`
5. Generate color-coded HTML with explanations for each component

## License

Free to use and modify. Made by robots. We're coming for you soon, so enjoy the free labour while you can.
