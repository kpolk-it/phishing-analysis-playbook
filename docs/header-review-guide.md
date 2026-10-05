# Email Header Review Guide

This is a beginner-friendly guide for reviewing common email header fields during phishing triage.

## What to Look For

### From / Reply-To
- Does the visible name match the actual address?
- Is the Reply-To different from the From address?
- Does the domain look like a lookalike of a trusted company?

### Return-Path
- Where would bounce messages go?
- Does this match the claimed sender?

### Received Lines
- Do the hops look unusual?
- Was the message received from an unexpected source?

### Authentication Results
Look for:
- SPF (Sender Policy Framework): Verifies the sending server's IP address is authorized by the domain in the smtp.mailform address via DNS TXT records. 
- DKIM (DomainKeys Identified Mail): Adds a digital cryptographic signature to the email header to confirm the message content was not altered in transit. 
- DMARC (Domain-based Message Authentication, Reporting and Comformance): Aligns SPF and DKIM results with the visible header from address, and instructs receiving servers to deliver, quarantine, or reject failing message.  

These results help show whether the sending domain is being used in a legitimate way. A failed or missing result does not automatically prove phishing, but it is useful context.

## Notes for Analysts

- You do not need to decode every header line during first-pass triage.
- Focus on sender mismatch, lookalike domains, unexpected links, and user action.
- If headers are confusing, document what you can and escalate with the original email attached.
