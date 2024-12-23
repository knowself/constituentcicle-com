# Constituent Circle Platform

<!-- BEGIN-PROTECT: PROJECT-PURPOSE -->
<!-- LAST-UPDATED: 2024-12-17T19:46:26-05:00 -->
<!-- REQUIRES-APPROVAL: VP-PRODUCT -->
## Project Purpose and Context
Constituent Circle is an AI technology platform (CC) designed to enhance multi-channel communication (email, SMS, and others) between representatives and their constituents. By leveraging artificial intelligence (AI) and natural language processing (NLP), the CC platform enables representatives to craft personalized, on-message communications efficiently while maintaining their authentic voice and personal touch. The goal is to facilitate meaningful, goal-oriented conversations at scale, across all communication channels, ensuring that constituents feel heard and represented.
<!-- END-PROTECT: PROJECT-PURPOSE -->

<!-- BEGIN-PROTECT: TECH-STACK -->
<!-- LAST-UPDATED: 2024-12-17T19:46:26-05:00 -->
<!-- REQUIRES-APPROVAL: TECH-LEAD -->
## Tech Stack Documentation

### Core Technologies
- **Frontend**: Next.js (v14) hosted on Vercel
- **Backend**: 
  - Firebase Cloud Functions
  - Vercel Edge Functions (for OpenAI)
  - Twilio API (for SMS)
- **Database**: Firestore
- **Authentication**: Firebase Auth
- **AI**: OpenAI via Vercel AI SDK
- **Messaging**: 
  - Email: Google Workspace & Firebase
  - SMS: Twilio API
- **Deployment**: Vercel Platform

### Key Dependencies
- **Authentication and Backend**
  - Firebase Admin SDK (Cloud-only mode)
  - Required: firebase-admin
  - Forbidden: @firebase/app, @firebase/auth, firebase, firebase-functions

- **Communication**
  - Twilio SDK
  - @twilio/conversations
  - Google Cloud Platform SDK

- **Styling and UI**
  - Tailwind CSS (v3.4.15)
  - @tailwindcss/typography
  - PostCSS & Autoprefixer

- **Development Tools**
  - TypeScript (v5.6.3)
  - ESLint with TypeScript parser
  - Prettier
  - Jest & React Testing Library

### Service Integration Flow
1. **Authentication Flow**
   - Firebase Auth handles user sessions
   - Role-based access stored in Firestore

2. **AI Communication Flow**
   - User requests handled by Vercel Edge Functions
   - OpenAI streaming responses via Vercel AI SDK
   - Results stored in Firestore via Firebase Functions

3. **Messaging Flow**
   - Email: Google Workspace & Firebase
   - SMS: Twilio API integration
   - Message queuing and scheduling
   - Delivery status tracking

4. **Data Management Flow**
   - Constituent data in Firestore
   - Heavy computations in Firebase Functions
   - Real-time updates via Firestore listeners
<!-- END-PROTECT: TECH-STACK -->

<!-- BEGIN-PROTECT: TIMELINE -->
<!-- LAST-UPDATED: 2024-12-17T19:46:26-05:00 -->
<!-- REQUIRES-APPROVAL: PROJECT-MANAGER -->
## 6-Week Launch Plan (Dec 17, 2024 - Jan 28, 2025)

### Progress Update (Dec 18, 2024)

#### Week 1 (Dec 18-24): Core Communication
- **Tasks Completed**:
  - Setup Vercel AI SDK + OpenAI
  - Implemented Twilio integration
  - Developed basic email and SMS composer UIs
  - Integrated AI assistance features, including message improvement and tone adjustment.

- **AI Assistance Integration Milestones**:
  1. **API Interaction Logic Implementation** (Deadline: Dec 20, 2024) - In progress.
  2. **Unified API Interface Creation** (Deadline: Dec 22, 2024) - In progress.
  3. **Response Aggregation Functionality** (Deadline: Dec 24, 2024) - Planned.
  4. **User Interface Design** (Deadline: Dec 26, 2024) - Planned.
  5. **Testing and Feedback Mechanism** (Deadline: Dec 28, 2024) - Planned.

#### Next Steps
- **Testing**: Validate the AI integration with the updated Google AI endpoint.
- **Continue with Remaining Milestones**: Focus on completing the milestones for the AI assistance integration as outlined in the roadmap.

### Week 1 (Dec 18-24): Core Communication
- [ ] Setup Vercel AI SDK + OpenAI
- [ ] Implement Twilio integration
- [ ] Basic email composer UI
- [ ] Basic SMS composer UI
- [ ] AI assistance integration
  - Message improvement
  - Tone adjustment
  - Simple templates
- [ ] Message preview & editing

### Mini Milestones for AI Assistance Integration

1. **API Interaction Logic Implementation**  
   - Develop the function for sequential API requests and error handling.  
   - Deadline: Dec 20, 2024  

2. **Unified API Interface Creation**  
   - Build the API wrapper class/module to manage interactions with both OpenAI and Google AI Studio.  
   - Deadline: Dec 22, 2024  

3. **Response Aggregation Functionality**  
   - Implement the function to combine responses from both APIs and prioritize them.  
   - Deadline: Dec 24, 2024  

4. **User Interface Design**  
   - Create a user-friendly interface to display aggregated suggestions.  
   - Deadline: Dec 26, 2024  

5. **Testing and Feedback Mechanism**  
   - Conduct testing of the integration and implement a feedback loop for users to rate suggestions.  
   - Deadline: Dec 28, 2024  

### Week 2 (Dec 25-31): Constituent Base
- [ ] Firestore constituent model
- [ ] Basic import/export (CSV)
- [ ] Simple search & filtering
- [ ] Basic segmentation (tags/groups)
- [ ] Communication preferences management

### Week 3 (Jan 1-7): Campaign Management
- [ ] Multi-channel campaign creation
- [ ] Basic scheduling system
- [ ] Simple analytics tracking
  - Email opens & clicks
  - SMS delivery & responses
  - Basic engagement metrics

### Week 4 (Jan 8-14): Admin & Polish
- [ ] Usage monitoring
  - Email volume tracking
  - SMS credit management
- [ ] Basic billing (Stripe)
- [ ] User onboarding flow
- [ ] Essential documentation

### Week 5 (Jan 15-21): Testing
- [ ] Internal testing
- [ ] 2-3 friendly offices beta
- [ ] Performance optimization
- [ ] Critical bug fixes
- [ ] Message delivery testing

### Week 6 (Jan 22-28): Launch
- [ ] Final security review
- [ ] Production deployment
- [ ] Initial customer onboarding
- [ ] Support system ready
- [ ] Communication monitoring
<!-- END-PROTECT: TIMELINE -->

<!-- BEGIN-PROTECT: AUTH-SYSTEM -->
<!-- LAST-UPDATED: 2024-12-17T19:46:26-05:00 -->
<!-- REQUIRES-APPROVAL: SECURITY-LEAD -->
## Authorization System

### Role Hierarchy

#### Company Staff (Platform Level)
- Completely separate from office staff
- Focused on platform management and support
- Roles:
  - Company Admin: Full platform access
  - Company Manager: Billing and major issues
  - Support Staff: Help when requested
  - Data Analyst: Platform-wide analytics

#### Representative Office Staff
- **Permanent Roles**
  - Representative: Elected official
  - Chief of Staff: Office management
  - Communications Director
  - Office Admin
  - Staff Member

- **Campaign & Temporary Staff**
  - Campaign Manager
  - Campaign Coordinator
  - Field Organizer
  - Volunteer Coordinator
  - Temporary Staff
  - Intern
  - Volunteer

### Employment Types
- Permanent: Regular full-time staff
- Temporary: Short-term staff
- Campaign: Campaign-specific staff
- Seasonal: Interns, seasonal workers
- Volunteer: Campaign volunteers

### Security Implementation
1. **Firebase Security Rules**
   - Role-based access control
   - Document-level security
   - Collection-level permissions

2. **Authentication Flow**
   - Email/Password and Google Sign-in
   - Role assignment and verification
   - Session management

3. **Data Access Control**
   - Office-level isolation
   - Role-based permissions
   - Temporary access management
   - Communication permissions
<!-- END-PROTECT: AUTH-SYSTEM -->

<!-- BEGIN-PROTECT: DEV-STANDARDS -->
<!-- LAST-UPDATED: 2024-12-17T19:46:26-05:00 -->
<!-- REQUIRES-APPROVAL: TECH-LEAD -->
## Development Guidelines

### Code Quality Standards
- Follow SOLID principles
- Implement proper error handling
- Write comprehensive tests
- Document all major components

### Security Best Practices
- No hard-coded credentials
- Input validation
- Data sanitization
- Proper error handling
- Regular security audits
- Secure message handling

### Performance Requirements
- Page load < 2s
- API response < 500ms
- Message delivery < 10s
- 90% uptime minimum
- Efficient database queries

### Documentation Requirements
- Code comments
- API documentation
- User guides
- Deployment guides
- Integration guides
<!-- END-PROTECT: DEV-STANDARDS -->

## Instructions for Using Serverless Functions

### Overview
This document provides instructions for implementing and managing serverless functions within the Constituent Circle platform. Serverless functions allow for executing code in response to events without the need for server management, enhancing scalability and reducing operational overhead.

### Setting Up Cloud Functions
1. **Choose a Cloud Provider**: Select between AWS Lambda or Google Cloud Functions based on your project requirements.
2. **Create a Function**: Follow the provider's documentation to create a new cloud function. Specify the trigger (e.g., HTTP request, Pub/Sub message).
3. **Deploy Your Code**: Upload your function code, ensuring it adheres to the provider's structure and requirements.
4. **Test the Function**: Use the cloud provider's testing tools to ensure your function behaves as expected.

### Best Practices
- **Keep Functions Lightweight**: Limit the complexity of each function to ensure quick execution and easy debugging.
- **Use Environment Variables**: Store sensitive information like API keys in environment variables to keep them secure.
- **Monitor Performance**: Utilize monitoring tools to track the performance of your cloud functions and set up alerts for any issues.

### Integration with Other Services
- **Database Integration**: Ensure your functions can interact with Firestore or other databases for data storage and retrieval.
- **Logging**: Implement logging within your functions to capture important events and errors for troubleshooting purposes.

<!-- BEGIN-PROTECT: VERSION -->
<!-- LAST-UPDATED: 2024-12-17T19:46:26-05:00 -->
<!-- REQUIRES-APPROVAL: TECH-LEAD -->
Last Updated: 2024-12-17T19:46:26-05:00
Version: 1.0.0
<!-- END-PROTECT: VERSION -->