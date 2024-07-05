<%` and `%>

<% expression %>

<%* code %>

<%_` and `_ %>

<%-` and `-%>

<%+`) to execute commands in preview mode.

### Key Modules and Functions

#### Config Module (`tp.config`)

Access Templater's running configuration, including:
- `tp.config.active_file?`
- `tp.config.run_mode`
- `tp.config.target_file`
- `tp.config.template_file`

#### Date Module (`tp.date`)

Functions related to date manipulation:
- **Current Date**: `<% tp.date.now(format?: string, offset?: number|string, reference?: string, reference_format?: string) %>

<% tp.date.tomorrow(format?: string) %>

<% tp.date.yesterday(format?: string) %>

<% tp.date.weekday(format: string, weekday: number, reference?: string, reference_format?: string) %>

<% tp.file.content %>

<%* await tp.file.create_new(template: TFile|string, filename?: string, open_new?: boolean, folder?: TFolder) %>

<% tp.file.creation_date(format?: string) %>

<% tp.file.cursor(order?: number) %>

<% await tp.file.exists(filepath: string) %>

<% tp.file.find_tfile(filename: string) %>

<% tp.file.include(include_link: string|TFile) %>

<% tp.file.last_modified_date(format?: string) %>

<% await tp.file.move(new_path: string, file_to_move?: TFile) %>

<% await tp.file.rename(new_title: string) %>

<% tp.file.selection() %>

<% tp.file.tags %>

<% tp.file.title %>

<% tp.frontmatter.<variable_name> %>

<% tp.frontmatter["variable name with spaces"] %>

<%* tp.hooks.on_all_templates_executed(callback_function: () => any) %>

<% app.vault.getAllLoadedFiles().filter(x => x instanceof tp.obsidian.TFolder).map(x => x.name) %>

<% tp.obsidian.normalizePath("Path/to/file.md") %>

<% tp.obsidian.htmlToMarkdown("<h1>Heading</h1><p>Paragraph</p>") %>

<%* const response = await tp.obsidian.requestUrl("https://jsonplaceholder.typicode.com/todos/1"); tR += response.json.title; %>

<% tp.system.clipboard() %>

<% tp.system.prompt(prompt_text?: string, default_value?: string, throw_on_cancel?: boolean, multiline?: boolean) %>

<% tp.system.suggester(text_items: string[]|((item: T) => string), items: T[], throw_on_cancel?: boolean, placeholder?: string, limit?: number) %>

<% tp.web.daily_quote() %>

<% tp.web.random_picture(size?: string, query?: string, include_size?: boolean) %>

<% tp.user.my_script("Hello World!") %>

<% tp.user.<user_function_name>({arg1: value1, arg2: value2}) %>

<% tp.file.creation_date() %>

<% tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>

<% tp.date.now("YYYY-MM-DD" -1) %>

<% tp.date.now("YYYY-MM-DD" 1) %>

<% tp.file.title %>

<% tp.web.daily_quote() %>

<%* if (tp.file.title.startsWith("Hello")) { %>

<%* } else { %>

<%* } %>