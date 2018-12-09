# Bug Bounty Tips

### IDOR

- when you're looking at an asset that may use a microservices architecture, look for IDOR vulnerabilities using path traversal. E.g. https://example/?id=1/../2.
