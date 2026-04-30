## Summary
This assessment evaluates VALR from a guest (unauthenticated) user perspective across:
- Frontend (UX + exploratory testing)
- Public API (market data validation)
- Authentication boundary (security testing)

## Tools Used
- Browser DevTools (network + UI inspection)
- Bruno (API testing)
- Manual exploratory testing

## Approach
I combined:
- Exploratory testing (to uncover usability risks)
- Structured test cases (to ensure coverage)
- API validation (data integrity + negative testing)
- Security probing (authentication boundary)

## Key Findings
- Public API is stable and consistent
- Authentication layer correctly rejects unauthenticated access
- Trading UI is powerful but overwhelming for first-time users
- Registration UX could be improved with proactive validation

## If I Had More Time
- Automate API tests (e.g., pytest / Newman)
- Performance testing (API latency under load)
- Deeper security testing (rate limiting, fuzzing)
- Cross-browser compatibility testing
