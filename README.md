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
- `evidence/` — Postman screenshots backing every finding in the
  report:
  - `test1_open_endpoint_users.png` — unauthenticated PII exposure
  - `test2_excessive_data_comments.png` — nested endpoint data exposure
  - `test3_idor_user1_posts.png` / `test4_idor_user2_posts_compare.png` — BOLA/IDOR
  - `test5_input_validation_outofrange_404.png` / `test6_input_validation_nonnumeric_404.png` — error handling (passed)
  - `test7_rate_limiting_response.png` / `test7b_headers_ratelimit_poweredby.png` / `test7c_headers_top_no_security_headers.png` — rate limiting & header checks
  - `test8_post_input_validation_write.png` — write-endpoint input validation

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
