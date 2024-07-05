<%*
  // Define the URL and link text
  const url = await tp.system.prompt("Enter the URL:");
  const linkText = await tp.system.prompt("Enter the link text:");

  // Define the file path and the header under which to add the URL
  const filePath = "Bookmarks/Obsidian References.md";
  const header = "### Your Header Name"; // Change this to your desired header

  // Define the frontmatter details
  const creationDate = tp.date.now("YYYY-MM-DD HH:mm");
  const topic = await tp.system.prompt("Enter the topic:");
  const category = await tp.system.prompt("Enter the category:");

  // Read the content of the file using app.vault.read
  let file = await app.vault.getAbstractFileByPath(filePath);
  if (!file) {
    throw new Error(`File "${filePath}" not found.`);
  }
  let fileContent = await app.vault.read(file);

  // Find the position of the header
  const headerPosition = fileContent.indexOf(header);
  if (headerPosition === -1) {
    throw new Error(`Header "${header}" not found in the file.`);
  }

  // Find the position after the header
  const afterHeaderPosition = fileContent.indexOf('\n', headerPosition) + 1;

  // Create the bookmark entry
  const bookmarkEntry = `[${linkText}](${url})\n`;

  // Insert the bookmark entry after the header
  fileContent = fileContent.slice(0, afterHeaderPosition) + bookmarkEntry + fileContent.slice(afterHeaderPosition);

  // Add frontmatter if not already present
  if (!fileContent.startsWith('---')) {
    fileContent = `---
creation_date: ${creationDate}
topic: ${topic}
category: ${category}
---
${fileContent}`;
  } else {
    // Update frontmatter if already present
    const frontmatterEnd = fileContent.indexOf('---', 3) + 3;
    const frontmatter = `---
creation_date: ${creationDate}
topic: ${topic}
category: ${category}
---\n`;
    fileContent = frontmatter + fileContent.slice(frontmatterEnd);
  }

  // Write the updated content back to the file using app.vault.write
  await app.vault.write(file, fileContent);
%>
