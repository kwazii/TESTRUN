function cloneFileToFolder() {
  // Replace these with your specific file and folder IDs
  const sourceFileId = "YOUR_SOURCE_FILE_ID"; // Static file ID
  const destinationFolderId = "YOUR_DESTINATION_FOLDER_ID"; // Static folder ID

  try {
    // Get the source file
    const sourceFile = DriveApp.getFileById(sourceFileId);
    if (!sourceFile) {
      throw new Error("Source file not found.");
    }

    // Get the destination folder
    const destinationFolder = DriveApp.getFolderById(destinationFolderId);
    if (!destinationFolder) {
      throw new Error("Destination folder not found.");
    }

    // Make a copy of the source file
    const clonedFile = sourceFile.makeCopy(destinationFolder);

    // Optional: Rename the cloned file
    clonedFile.setName(`Cloned - ${sourceFile.getName()}`);

    Logger.log(`File cloned successfully: ${clonedFile.getName()}`);
  } catch (e) {
    Logger.log(`Error: ${e.message}`);
  }
}