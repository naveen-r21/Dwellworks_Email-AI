# Email AI Automation

An AI-powered email analysis tool that processes emails from Microsoft Graph API.


## Installation

1. Clone the repository
2. Install the required packages: `pip install -r requirements.txt`
3. Run the application: `streamlit run app.py`

## Features

- Fetch emails from Microsoft Graph API
- Process and analyze emails using AI
- Display results with metrics
- Download analysis reports

## Email Threading

The application uses an improved method for organizing email threads based on the relationship between messages:

### Thread Organization

- Emails are linked using `internetMessageId` and `inReplyTo` fields
- Each message has a globally unique ID (`internetMessageId`)
- Reply messages contain a reference to their parent message (`inReplyTo`)
- This builds a proper hierarchical thread structure

### Benefits

- More accurate thread reconstruction compared to using just conversation IDs
- Works for large threads (50-100+ emails) with O(n) complexity
- Clear visualization of thread hierarchy in the UI
- Resilient to various email client formatting differences

The thread structure is visualized in the main interface, showing the parent-child relationships between messages with proper indentation.

## Email Threading Improvements

### Subject-Based Thread Grouping

The application now includes an improved method for organizing email threads based on subject similarity:

- Groups emails with similar subjects together, even when conversation IDs differ
- Uses fuzzy matching to handle minor variations in subject lines (85% similarity threshold)
- Properly handles "Re:" prefixed replies as part of the same thread
- More intuitive thread organization that matches how users think about emails

### Metadata Cleaning

Email content is now cleaned more effectively:

- Removes metadata and signatures by cutting content after "from:" appears
- Preserves important information like property details, dates, and times
- Improves AI analysis by focusing on the actual email message
- Removes disclaimers, forwarded content, and other noise

These improvements make the application more reliable when working with emails from different sources or email clients that may handle threading differently.

## License

This project is licensed under the MIT License.
