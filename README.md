# HR Chatbot for Zoho SalesIQ

An intelligent conversational HR Chatbot built for Zoho SalesIQ with automatic follow-up message generation. This bot helps HR departments engage with job seekers through natural conversations that automatically continue until users explicitly end the chat.

## Features

### 1. Conversational Follow-ups
- **Automatic continuation**: After every bot response, a contextual follow-up message is automatically generated
- **Natural flow**: Follow-ups are relevant to user input or bot responses
- **User control**: Users can explicitly end conversation at any time
- **Smart detection**: Bot detects end-of-conversation signals and stops sending follow-ups immediately

### 2. Core HR Functions
- **Apply for Jobs**: Users can browse job listings and apply directly through the bot
- **Find a Job**: Smart job matching based on user skills and preferences
- **My Jobs**: Track previously applied jobs and their statuses
- **OTP Verification**: Secure phone number verification for applications

### 3. Data Handling
- **Job Carousel Cards**: Beautiful presentation of job listings with Apply/Details actions
- **Form Collection**: Gathers name, email, phone, resume, and other required information
- **Job Status Tracking**: Shows application status and upcoming interview events
- **Related Job Suggestions**: If application rejected, suggests similar positions

### 4. Advanced Features
- **OAuth 2.0 Integration**: Secure third-party HR software integration
- **AI Enhancements**: AI-powered job recommendations and matching
- **Real-time Updates**: Live job status and event tracking

## Architecture

### Technology Stack
- **Platform**: Zoho SalesIQ
- **Language**: Deluge (Zoho's scripting language)
- **Integration**: Third-party HR systems (Zoho Recruit, Bullhorn, Workable, etc.)

### Bot Flow
```
User Input → Intent Detection → Process Request → Generate Main Response
    ↓
Check Follow-up Status → Generate Contextual Follow-up → Send Both Messages
    ↓
Check for End Signal → Continue or End Conversation
```

## Installation & Setup

### Prerequisites
- Zoho SalesIQ account
- Access to HR third-party systems (Zoho Recruit, Bullhorn, etc.)
- Basic knowledge of Deluge scripting

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/Kaveeshwar18/HR-Chatbot-SalesIQ.git
   cd HR-Chatbot-SalesIQ
   ```

2. **Create a new bot in SalesIQ**
   - Navigate to SalesIQ Dashboard
   - Create a new bot
   - Copy the bot script from `bot/hr_chatbot.deluge`

3. **Configure integrations**
   - Set up OAuth 2.0 credentials for HR systems
   - Add API endpoints to `config/integrations.json`
   - Update database connection strings if needed

4. **Deploy**
   - Paste the complete script into SalesIQ bot builder
   - Test with sample queries
   - Enable on your website

## Usage Examples

### Scenario 1: User Applies for a Job
```
User: "Hi, I want to apply for a job"
Bot: "Great! I'd love to help you find the perfect job. Let me show you some available positions. What's your experience level? (Entry Level / Mid-Level / Senior)"
User: "Entry Level"
Bot: "Perfect! Here are some Entry Level positions matching your profile. [Job Cards]. Would you like to apply for any of these positions?"
User: "I'll apply for the Software Developer position"
Bot: "Excellent! Let me collect your details. What's your full name?"
```

### Scenario 2: Conversation Ends
```
User: "I think that's all for now, thanks!"
Bot: "You're welcome! I hope I could help. If you need anything else later, just let me know. Have a great day!"
[No follow-ups sent after this]
```

## Follow-up Message Logic

### When Follow-ups Are Generated
- After greeting messages
- After providing job information
- After form submissions
- After status checks

### When Follow-ups Stop
- User sends: "stop", "end chat", "that's all", "bye", "nothing else", "no thanks", "exit"
- Session flag is set to `followup_enabled = false`
- Further messages get only main response, no follow-ups

## Code Structure

```
hr-chatbot-salesiq/
├── bot/
│   ├── hr_chatbot.deluge          # Main bot script
│   ├── followup_engine.deluge      # Follow-up generation logic
│   ├── intent_detector.deluge      # Intent detection
│   └── job_handler.deluge          # Job-related operations
├── config/
│   ├── integrations.json           # Third-party API configs
│   └── settings.json               # Bot settings
├── docs/
│   ├── INSTALLATION.md
│   ├── API_REFERENCE.md
│   └── TROUBLESHOOTING.md
└── README.md
```

## API Integration

Supported HR Systems:
- Zoho Recruit
- Bullhorn
- Workable
- Jobdiva
- Ceipal
- JazzHR
- Vincere
- iCIMS
- JobAdder

## Testing

### Manual Testing Checklist
- [ ] Bot responds to greeting messages
- [ ] Follow-ups are generated after each main response
- [ ] Each follow-up is contextually relevant
- [ ] "Stop" commands prevent further follow-ups
- [ ] Job carousel displays correctly
- [ ] Apply form collects all required fields
- [ ] OTP verification works
- [ ] Job status tracking displays correctly
- [ ] Related job suggestions appear on rejection

## Troubleshooting

### Common Issues

1. **Follow-ups not appearing**
   - Check if `followup_enabled` flag is true in session
   - Verify bot response generation completes successfully
   - Check SalesIQ logs for errors

2. **Bot stops responding**
   - Verify API connections to HR systems
   - Check rate limiting on third-party APIs
   - Review Deluge script for syntax errors

3. **Job data not loading**
   - Verify API credentials in integrations.json
   - Check network connectivity
   - Ensure OAuth tokens are valid

## Performance Metrics

Target KPIs:
- Average conversation length: 4-6 turns
- User satisfaction: >85%
- Job application completion rate: >70%
- Response time: <2 seconds

## Brownie Points Implementation

✅ Related job suggestions on rejection
✅ OAuth 2.0 authentication
✅ AI-powered job recommendations
✅ Conversational follow-ups (Main Feature)

## Contributors

- **Developer**: Kaveeshwar18
- **Platform**: Zoho (Cliqtrix 2025 Contest Submission)

## License

MIT License - See LICENSE.md for details

## Contact & Support

For questions or support, please contact: [contact@cliqtrix.com](mailto:contact@cliqtrix.com)

## Acknowledgments

This project was developed for the Zoho Cliqtrix 2025 coding contest, focusing on innovative HR chatbot solutions for SalesIQ.
