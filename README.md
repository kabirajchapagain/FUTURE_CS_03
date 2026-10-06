# API Security Risk Analysis

Cyber Security Task 3 — Future Interns

## Overview

This repository contains a read-only API security risk analysis of
[JSONPlaceholder](https://jsonplaceholder.typicode.com), a public demo
REST API, performed the way a security consultant would assess a
client's SaaS API — identifying risks, assessing authentication and
access control, and documenting findings with business impact and
remediation guidance.

## Contents

- `API_Security_Risk_Analysis_Report.pdf` — full report: scope &
  ethics, methodology, API tested, risk classification framework,
  7 findings (with evidence and remediation), one tested-and-passed
  control, summary table, and remediation priorities.
- `Evidence/` — 10 Postman screenshots backing every finding in the
  report (open endpoint exposure, nested data exposure, IDOR/BOLA
  comparison, input validation on invalid IDs, rate-limit headers,
  missing security headers, and write-endpoint validation). Each
  screenshot is referenced as a numbered figure inside the report
  PDF, in the order it was captured.

## Tools Used

- [Postman](https://www.postman.com) — all requests sent and inspected here
- Manual review of response bodies, status codes, and headers

## Scope & Ethics

- Testing was performed only against JSONPlaceholder, a public API
  explicitly intended for testing and learning.
- Only read-only (GET) requests and safe POST requests (which this
  API fakes without persisting data) were used.
- No exploitation, bypass attempts, flooding/DoS testing, or access
  to private/production systems was performed.

## Methodology

1. Test endpoints with no credentials supplied to check for
   unauthenticated access.
2. Compare the same request across different numeric resource IDs to
   test for broken object-level authorization (IDOR/BOLA).
3. Submit a write request with unexpected data types and unescaped
   content to test input validation.
4. Request out-of-range and non-numeric IDs to test error handling.
5. Send repeated requests and inspect rate-limit headers.
6. Review all response headers for missing security headers and
   information disclosure.
7. Classify each finding as Low / Medium / High severity, with
   business impact and remediation for each.

## Disclaimer

This work is for security education purposes only, performed against
a public demo API with no real user data. No private or production
systems were tested.
