 const data = await tp.web.requestUrl("https://jsonplaceholder.typicode.com/posts/1"); tR += `Title: ${data.json.title}`; %>
   ```
   Fetches JSON data from an API and outputs a specific field.

### User Functions

#### Script User Functions

1. **Define and Use a Function**:
   ```javascript
   function greet(name) {
     return `Hello, ${name}!`;
   }
   module.exports = greet;
   ```

   ```markdown
   <% tp.user.greet("Alice") %>
   ```
   Invokes the `greet` function defined in a script.

2. **Math Function**:
   ```javascript
   function add(a, b) {
     return a + b;
   }
   module.exports = add;
   ```

   ```markdown
   Sum: <% tp.user.add(5, 10) %>
   ```
   Invokes the `add` function to output the sum of 5 and 10.

3. **Date Formatting Function**:
   ```javascript
   function formatDate(date) {
     return new Date(date).toLocaleDateString();
   }
   module.exports = formatDate;
   ```

   ```markdown
   Formatted Date: <% tp.user.formatDate(tp.date.now()) %>
   ```
   Invokes the `formatDate` function to format the current date.

4. **Custom Greeting Function**:
   ```javascript
   function customGreeting(name, timeOfDay) {
     return `Good ${timeOfDay}, ${name}!`;
   }
   module.exports = customGreeting;
   ```

   ```markdown
   <% tp.user.customGreeting("Bob", "morning") %>
   ```
   Invokes the `customGreeting` function with custom arguments.

5. **Temperature Conversion Function**:
   ```javascript
   function toCelsius(fahrenheit) {
     return (fahrenheit - 32) * 5 / 9;
   }
   module.exports = toCelsius;
   ```

   ```markdown
   Temperature in Celsius: <% tp.user.toCelsius(68) %>
   ```
   Invokes the `toCelsius` function to convert 68°F to Celsius.

#### System Command User Functions

1. **Define and Use a System Command**:
   ```markdown
   <% tp.user.systemCommand({ command: "ls", args: ["-l"] }) %>
   ```
   Executes the `ls -l` command and outputs the result.

2. **System Command with Input**:
   ```markdown
   <% tp.user.systemCommand({ command: "echo", args: ["Hello, World!"] }) %>
   ```
   Executes the `echo` command with a string input.

3. **Fetch System Info**:
   ```markdown
   <% tp.user.systemCommand({ command: "uname", args: ["-a"] }) %>
   ```
   Executes the `uname -a` command to fetch system information.

4. **Directory Listing**:
   ```markdown
   <% tp.user.systemCommand({ command: "ls", args: ["/path/to/directory"] }) %>
   ```
   Lists files in a specified directory.

5. **System Uptime**:
   ```markdown
   <% tp.user.systemCommand({ command: "uptime" }) %>
   ```
   Executes the `uptime` command to get system uptime information.

---

This comprehensive set of examples covers a variety of use cases and should help you utilize the Templater plugin effectively in Obsidian. If you need further assistance or have any specific questions, feel free to ask!