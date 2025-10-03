# Website Forms Documentation

## Overview

This website features multiple forms accessible through popup modals. All forms are integrated with Netlify Forms for data collection and storage. The forms are designed with modern UI/UX and include spam protection via honeypot fields.

## How Popup Forms Work

The website uses a modal-based system for forms. When a user clicks on a footer link or button, a modal overlay appears containing the relevant form. The modal can be closed by:

- Clicking the X button in the top-right corner
- Clicking outside the modal area
- Completing form submission (which triggers a success state)

All modals prevent body scrolling when open and restore it when closed.

## Form Data Storage

All form submissions are handled by Netlify Forms and stored in the Netlify dashboard. Each form has a unique `form-name` attribute that creates separate collections in Netlify:

- `dmca-removal` - DMCA takedown requests
- `movie-request` - Movie request submissions
- `report-issue` - Issue reports
- `contact-us` - General contact messages

Data is stored securely and can be exported from the Netlify admin panel.

## Forms Documentation

### 1. DMCA Removal Request Form

**Access:** Click "File DMCA Takedown Request" button or "Removal Request" in footer

**Purpose:** Submit Digital Millennium Copyright Act takedown notices

#### Fields:

1. **Full Name** (required)
   - Type: Text input
   - Purpose: Legal name of the complainant
   - Validation: Required, non-empty

2. **Email Address** (required)
   - Type: Email input
   - Purpose: Contact email for the complainant
   - Validation: Required, valid email format

3. **Phone Number** (optional)
   - Type: International phone input
   - Purpose: Additional contact method
   - Features: Supports all country codes via intl-tel-input library
   - Validation: Valid international format if provided

4. **Address** (optional)
   - Type: Textarea
   - Purpose: Physical address for legal correspondence

5. **Copyright Owner** (required)
   - Type: Text input
   - Purpose: Name of the copyright holder
   - Validation: Required, non-empty

6. **Description of Copyrighted Work** (required)
   - Type: Textarea
   - Purpose: Detailed description of the copyrighted material
   - Validation: Required, non-empty

7. **Original Location of Copyrighted Work** (required)
   - Type: Text input
   - Purpose: Where the original work is legitimately hosted
   - Validation: Required, non-empty

8. **URL(s) of Infringing Content** (required)
   - Type: Textarea
   - Purpose: Links to the infringing content on this website
   - Validation: Required, non-empty

9. **Providing Link from Our Website?** (radio buttons)
   - Options: Yes/No
   - Purpose: Determines if replacement link field should appear

10. **Real Movie Link (conditional)** (optional)
    - Type: Text input
    - Purpose: Legitimate source to replace infringing content
    - Appears when "Yes" is selected above

11. **Legal Statements** (required checkboxes)
    - Good Faith Belief: Acknowledges unauthorized use belief
    - Accurate Information: Confirms information accuracy under penalty of perjury
    - Understanding of Perjury: Acknowledges legal consequences of false claims
    - Timeline Acknowledgment: Confirms understanding of 24-48 hour processing time

12. **Electronic Signature** (required)
    - Type: Text input
    - Purpose: Digital signature binding under ESIGN Act
    - Validation: Required, matches full name

#### Spam Protection:
- Honeypot field: Hidden input named "bot-field"

#### Submission:
- Form data sent to Netlify
- Success modal displayed with countdown timer
- Form resets after submission

### 2. Movie Request Form

**Access:** Click "Movie Request" in footer

**Purpose:** Allow users to request movies to be added to the collection

#### Fields:

1. **Movie Title** (required)
   - Type: Text input
   - Purpose: Name of the requested movie
   - Validation: Required, non-empty

2. **Release Year** (optional)
   - Type: Number input
   - Purpose: Year the movie was released

3. **Why do you want this movie?** (optional)
   - Type: Textarea
   - Purpose: User's reason for requesting the movie

4. **Name** (required)
   - Type: Text input
   - Purpose: Requester's name
   - Validation: Required, non-empty

5. **Email** (required)
   - Type: Email input
   - Purpose: Requester's contact email
   - Validation: Required, valid email format

#### Spam Protection:
- Honeypot field: Hidden input named "bot-field"

### 3. Report Issue Form

**Access:** Click "Report Issue" in footer

**Purpose:** Allow users to report technical issues or broken content

#### Fields:

1. **Issue Type** (required)
   - Type: Select dropdown
   - Options: Broken Link, Video Quality Issue, Audio Problem, Subtitle Issue, Loading Error, Other
   - Purpose: Categorize the type of issue
   - Validation: Required selection

2. **Page URL** (required)
   - Type: URL input
   - Purpose: Link to the page where the issue occurs
   - Validation: Required, valid URL format

3. **Description** (required)
   - Type: Textarea
   - Purpose: Detailed explanation of the issue
   - Validation: Required, non-empty

4. **Name** (optional)
   - Type: Text input
   - Purpose: Reporter's name

5. **Email** (optional)
   - Type: Email input
   - Purpose: Reporter's contact email
   - Validation: Valid email format if provided

#### Spam Protection:
- Honeypot field: Hidden input named "bot-field"

### 4. Contact Us Form

**Access:** Click "Contact Us" in footer

**Purpose:** General contact form for user inquiries

#### Fields:

1. **Subject** (required)
   - Type: Text input
   - Purpose: Brief description of the inquiry
   - Validation: Required, non-empty

2. **Message** (required)
   - Type: Textarea
   - Purpose: Detailed message content
   - Validation: Required, non-empty

3. **Name** (required)
   - Type: Text input
   - Purpose: Sender's name
   - Validation: Required, non-empty

4. **Email** (required)
   - Type: Email input
   - Purpose: Sender's contact email
   - Validation: Required, valid email format

#### Spam Protection:
- Honeypot field: Hidden input named "bot-field"

### 5. FAQ / Help Center

**Access:** Click "FAQ / Help Center" in footer

**Purpose:** Display frequently asked questions and help information

**Content:** Static informational modal containing:
- How to watch movies
- Audio troubleshooting
- Subtitle instructions
- Copyright reporting process
- Movie request information
- Broken link reporting

**Features:**
- No form submission
- Link to Contact Us form for additional help

### 6. DMCA Notice

**Access:** Click "DMCA Notice" in footer

**Purpose:** Display DMCA policy and contact information

**Content:** Static informational modal containing:
- Explanation of DMCA
- Website's DMCA policy
- Required information for takedown notices
- Processing timeline
- Counter-notification process
- Designated DMCA agent contact

**Features:**
- No form submission
- Direct contact information for DMCA agent

## Technical Implementation

### Modal System
- Uses CSS classes to show/hide modals
- Prevents body scrolling during modal display
- Click-outside-to-close functionality
- Responsive design for mobile devices

### Form Validation
- Client-side validation for required fields
- Real-time validation feedback
- Email format validation
- Custom validation for international phone numbers

### Netlify Integration
- All forms use `data-netlify="true"`
- Unique form names for data organization
- Honeypot spam protection
- Automatic form handling and storage

### International Phone Support
- Uses intl-tel-input library
- Supports all country codes
- Auto-detects user's country
- Validates international number formats

## Security Features

1. **Honeypot Fields:** Hidden inputs to catch spam bots
2. **Input Sanitization:** Client-side validation prevents malformed data
3. **CSRF Protection:** Handled by Netlify's form processing
4. **Data Encryption:** All data transmitted securely to Netlify

## Accessibility

- Proper label associations for screen readers
- Keyboard navigation support
- High contrast error states
- Clear visual feedback for form states
- Responsive design for various screen sizes

## Maintenance

- Form data accessible via Netlify dashboard
- Export capabilities for data analysis
- Spam filtering through honeypot detection
- Regular monitoring recommended for form submissions
