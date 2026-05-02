Build a production-quality web application.

Core engineering rules
- Do not write throwaway code, throwaway schema, or prototype architecture.
- Prefer boring, explicit, maintainable architecture over clever abstractions.
- Optimise for long-term maintainability, testability, and extensibility.
- Keep domain logic, infrastructure, and UI concerns clearly separated.
- Use explicit schema, explicit statuses/enums, and clear migrations.
- Keep code strongly typed and easy to reason about.
- Do not overbuild speculative features.

Framework and platform
- Framework target: Remix 3
- Language: TypeScript
- Infrastructure as code: AWS CDK in TypeScript
- Deployment target: AWS
- Likely runtime target: AWS Lambda
- Authentication: Cognito
- Email: SES
- Use environment variables for runtime/app config where appropriate
- Use GitHub Secrets for CI/CD and deployment secrets
- Keep infrastructure modular and replaceable
- Design cleanly for Lambda, but do not hardcode assumptions that would prevent moving to another AWS runtime later

Database strategy
- Long-term database target: PostgreSQL on AWS RDS
- Do not assume expensive always-on infrastructure for initial deployment
- Design schema, migrations, and data access around PostgreSQL compatibility from day one
- Keep migration to RDS straightforward
- Do not design the app around a temporary non-relational store

Frontend and UX
- Optimise for clarity, calmness, speed, and practical usability
- Prioritise phone-friendly UX where relevant
- Do not overcomplicate theming in v1 unless required
- Basic branding support is fine, but avoid premature theme systems

CSS structure
- Each route or component should have its own CSS file unless styles are clearly shared
- Shared styles should live in explicit shared files
- Avoid a giant global CSS file
- Keep styling modular and maintainable

Testing and validation
- Include automated testing appropriate for the architecture
- Use Playwright for end-to-end testing
- Include route-level screen capture / screenshot validation where practical
- Prioritise screenshot validation for major user-facing flows
- Validate not only APIs but also real UI states and route flows

Delivery expectations
- Start with architecture and schema
- Critique the architecture for overengineering and weak spots
- Then provide implementation plan
- Then implement
- Keep the output practical, not academic