## 

### Introduction

Templater is a powerful templating language for Obsidian that allows users to insert variables, execute functions, and run JavaScript code within their notes. This guide aims to provide you with the necessary knowledge to become a Templater power user, covering installation, key concepts, and practical examples.

### Installation

1. **Install Templater**: Go to the Community Plugins tab within Obsidian, search for "Templater," and install it.
2. **Restart Obsidian**: It's good practice to restart the app after installation to ensure everything is working properly.

### Terminology

- **Template**: A file containing commands.
- **Command**: A text snippet enclosed in `<%` and `%>`.
- **Function**: An object invoked inside a command that returns a value.

### Command Types

1. **Interpolation Command**: Outputs the result of the expression inside. Syntax: `<% expression %>`.
2. **JavaScript Execution Command**: Executes JavaScript code inside. Syntax: `<%* code %>`.

### Command Utilities

- **Whitespace Control**: Manage newlines and spaces around commands.
  - `<%_` and `_ %>`: Trim all whitespace before or after the command.
  - `<%-` and `-%>`: Trim one newline before or after the command.

### Dynamic Commands

- Add a `+` after the opening tag (`<%+`) to execute commands in preview mode.

### Key Modules and Functions

#### Config Module (`tp.config`)

Access Templater's running configuration, including:
- `tp.config.active_file?`
- `tp.config.run_mode`
- `tp.config.target_file`
- `tp.config.template_file`

#### Date Module (`tp.date`)

Functions related to date manipulation:
- **Current Date**: `<% tp.date.now(format?: string, offset?: number|string, reference?: string, reference_format?: string) %>`
- **Tomorrow's Date**: `<% tp.date.tomorrow(format?: string) %>`
- **Yesterday's Date**: `<% tp.date.yesterday(format?: string) %>`
- **Weekday**: `<% tp.date.weekday(format: string, weekday: number, reference?: string, reference_format?: string) %>`

#### File Module (`tp.file`)

Functions related to file manipulation:
- **File Content**: `<% tp.file.content %>`
- **Create New File**: `<%* await tp.file.create_new(template: TFile|string, filename?: string, open_new?: boolean, folder?: TFolder) %>`
- **Creation Date**: `<% tp.file.creation_date(format?: string) %>`
- **Cursor Position**: `<% tp.file.cursor(order?: number) %>`
- **File Exists**: `<% await tp.file.exists(filepath: string) %>`
- **Find File**: `<% tp.file.find_tfile(filename: string) %>`
- **Include File**: `<% tp.file.include(include_link: string|TFile) %>`
- **Last Modified Date**: `<% tp.file.last_modified_date(format?: string) %>`
- **Move File**: `<% await tp.file.move(new_path: string, file_to_move?: TFile) %>`
- **Rename File**: `<% await tp.file.rename(new_title: string) %>`
- **Retrieve Selection**: `<% tp.file.selection() %>`
- **Retrieve Tags**: `<% tp.file.tags %>`
- **Retrieve Title**: `<% tp.file.title %>`

#### Frontmatter Module (`tp.frontmatter`)

Access frontmatter variables:
- `<% tp.frontmatter.<variable_name> %>`
- `<% tp.frontmatter["variable name with spaces"] %>`

#### Hooks Module (`tp.hooks`)

Execute code on Templater events:
- **On All Templates Executed**: `<%* tp.hooks.on_all_templates_executed(callback_function: () => any) %>`

#### Obsidian Module (`tp.obsidian`)

Access functions and classes from the Obsidian API:
- **Get All Folders**: `<% app.vault.getAllLoadedFiles().filter(x => x instanceof tp.obsidian.TFolder).map(x => x.name) %>`
- **Normalize Path**: `<% tp.obsidian.normalizePath("Path/to/file.md") %>`
- **HTML to Markdown**: `<% tp.obsidian.htmlToMarkdown("<h1>Heading</h1><p>Paragraph</p>") %>`
- **HTTP Request**: `<%* const response = await tp.obsidian.requestUrl("https://jsonplaceholder.typicode.com/todos/1"); tR += response.json.title; %>`

#### System Module (`tp.system`)

System-related functions:
- **Clipboard**: `<% tp.system.clipboard() %>`
- **Prompt**: `<% tp.system.prompt(prompt_text?: string, default_value?: string, throw_on_cancel?: boolean, multiline?: boolean) %>`
- **Suggester**: `<% tp.system.suggester(text_items: string[]|((item: T) => string), items: T[], throw_on_cancel?: boolean, placeholder?: string, limit?: number) %>`

#### Web Module (`tp.web`)

Functions related to web requests:
- **Daily Quote**: `<% tp.web.daily_quote() %>`
- **Random Picture**: `<% tp.web.random_picture(size?: string, query?: string, include_size?: boolean) %>`

### User Functions

#### Script User Functions

Create JavaScript functions and call them as user functions:
1. **Define a Script User Function**: Place your script in the specified script folder (e.g., `Scripts/my_script.js`).
2. **Example Script**:
   ```javascript
   function my_function(msg) {
     return `Message from my script: ${msg}`;
   }
   module.exports = my_function;
   ```
3. **Invoke the Function**: `<% tp.user.my_script("Hello World!") %>`

#### System Command User Functions

Execute system commands and retrieve their output:
1. **Enable System Commands**: Enable system commands in Templater's settings.
2. **Define a System Command User Function**: Go to settings and add a user function associated with a system command.
3. **Invoke the Function**: `<% tp.user.<user_function_name>({arg1: value1, arg2: value2}) %>`

### Example Templates

1. **Basic Template**:
   ```markdown
   ---
   creation date: <% tp.file.creation_date() %>
   modification date: <% tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>
   ---

   << [[<% tp.date.now("YYYY-MM-DD" -1) %>]] | [[<% tp.date.now("YYYY-MM-DD" 1) %>]] >>

   # <% tp.file.title %>

   <% tp.web.daily_quote() %>
   ```

2. **JavaScript Execution Command**:
   ```markdown
   <%* if (tp.file.title.startsWith("Hello")) { %>
   This is a hello file!
   <%* } else { %>
   This is a normal file!
   <%* } %>
   ```

### Conclusion

This guide provides a comprehensive overview of the Templater plugin for Obsidian. By understanding and utilizing the functions and examples provided, you can create powerful templates to automate tasks and enhance your note-taking experience.