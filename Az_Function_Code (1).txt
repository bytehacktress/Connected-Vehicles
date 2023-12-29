// Exporting an asynchronous function as the entry point for the Azure Function
module.exports = async function (context, myBlob) {
    // Logging a message indicating that the function is processing the blob
    context.log("JavaScript blob trigger function processed blob \n Blob:");
    context.log("********Azure Function Started********");

    // Initializing a variable to track the result of the processing (assuming success initially)
    var result = true;

    try {
        // Logging the content of the blob
        context.log(myBlob.toString());

        // Attempting to parse the blob content as JSON
        JSON.parse(myBlob.toString().trim().replace('\n', ' '));

    } catch (exception) {
        // Handling an exception if JSON parsing fails and updating the result variable
        context.log(exception);
        result = false;
    }

    // Checking the result of the processing
    if (result) {
        // If successful, copy the blob content to the staging folder
        context.bindings.stagingFolder = myBlob.toString();
        context.log("********File Copied to Staging Folder Successfully********");
    } else {
        // If unsuccessful (invalid JSON), copy the blob content to the rejected folder
        context.bindings.rejectedFolder = myBlob.toString();
        context.log("********Invalid JSON File Copied to Rejected Folder Successfully********");
    }

    // Logging a message indicating the end of the Azure Function
    context.log("*******Azure Function Ended Successfully*******");
};
