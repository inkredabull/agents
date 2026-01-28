---
name: boss-finder
description: Identify the person and their LinkedIn profile that a job posting role reports to. Use when the user provides a job posting URL and wants to know who the hiring manager or direct supervisor is. Automatically fetches job postings, extracts company name and reporting structure, then searches LinkedIn to find the specific person.
---

# Boss Finder

## Overview

This skill identifies who a job posting role reports to by fetching the job posting, extracting the company and reporting structure, then searching LinkedIn to find the specific person and their profile URL.

## Workflow

Follow these steps in order:

### Step 1: Fetch the Job Posting

Use `web_fetch` to retrieve the job posting content from the provided URL.

### Step 2: Extract Key Information

From the job posting, identify:
- **Company name**: Extract the company name from the posting
- **Reporting structure**: Look for phrases like "reports to", "reporting to", "will report to", or similar language that indicates the role's manager

### Step 3: Confirm Company Name

Before searching LinkedIn, confirm you've correctly identified the company name. If the company name is ambiguous or unclear from the URL or posting content, extract it from the job posting text.

### Step 4: Search LinkedIn for the Manager

Construct a LinkedIn search query in the format: `[Company Name] [Title]`

For example:
- "Linear Head of Engineering"
- "Acme Corp VP of Sales"
- "TechStartup Director of Product"

Use `web_search` with this query to find the person's LinkedIn profile.

### Step 5: Return Results with Confidence Level

Return the results in one of these formats based on what you found:

**When a specific person is found:**
```
Reports to: [Person Name]
LinkedIn: [LinkedIn Profile URL]
```

**When only the title is known:**
```
Reports to: [Title] (specific person not found)
Company: [Company Name]
```

**When reporting structure is unclear:**
```
Reporting structure: Not clearly specified in job posting
Company: [Company Name]
```

### Step 6: Handle Multiple Reporting Lines

If the job posting mentions multiple people the role reports to (e.g., "reports to VP of Engineering and dotted line to CTO"), only return information about the **primary** reporting relationship (the first one mentioned or the solid-line manager).

## Tips

- Job postings often use standard phrases: "This role reports to", "Reporting to the", "You will report to"
- Sometimes the reporting structure is in a "What you'll do" or "About the role" section
- If the company uses a different name on LinkedIn than in the job posting (e.g., "Acme" vs "Acme Corporation"), try variations
- LinkedIn search works best with exact titles as they appear on LinkedIn profiles
