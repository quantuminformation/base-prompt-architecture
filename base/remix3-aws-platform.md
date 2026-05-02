# Base Prompt: Remix 3 AWS Platform

## Usage

Use this as the reusable engineering baseline for app-specific prompts.

App-specific prompts should:
- link to this file at the top
- inherit these platform rules
- define only domain-specific product requirements
- avoid repeating base architecture rules unless overriding them

## Core engineering rules

Build a production-quality web application.

- Do not write throwaway code, throwaway schema, or prototype architecture.
- Prefer boring, explicit, maintainable architecture over clever abstractions.
- Optimise for long-term maintainability, testability, and extensibility.
- Keep domain logic, infrastructure, and UI concerns clearly separated.
- Use explicit schema, explicit statuses/enums, and clear migrations.
- Keep code strongly typed and easy to reason about.
- Do not overbuild speculative features.
- Do not hide important business logic inside UI components.
- Do not skip migrations or schema constraints because this is v1.

## Framework and platform

- Framework target: Remix 3
- Language: TypeScript
- Infrastructure as code: AWS CDK in TypeScript
- Deployment target: AWS
- Likely runtime target: AWS Lambda
- Authentication: Cognito
- Email: SES
- Use environment variables for runtime/app config where appropriate
- Use GitHub Secrets for CI/CD and deployment secrets
- Do not hardcode secrets
- Keep infrastructure modular and replaceable
- Design cleanly for Lambda, but do not hardcode assumptions that would prevent moving to another AWS runtime later

## Database strategy

- Long-term database target: PostgreSQL on AWS RDS
- Do not assume expensive always-on infrastructure for initial deployment
- The app may use a lower-cost interim database setup before RDS, but schema and migrations must remain PostgreSQL-compatible
- Design schema, migrations, and data access around PostgreSQL compatibility from day one
- Keep migration to RDS straightforward
- Do not design the app around a temporary non-relational store

## Frontend and UX

- Optimise for clarity, calmness, speed, and practical usability
- Prioritise phone-friendly UX where relevant
- Do not overcomplicate theming in v1 unless required
- Basic branding support is fine, but avoid premature theme systems
- Let the first visual design be clean, practical, and easy to change later

## CSS structure

- Each route or component should have its own CSS file unless styles are clearly shared
- Shared styles should live in explicit shared files
- Avoid one giant global CSS file
- Keep styling modular and maintainable
- Do not create scattered duplicate CSS rules when a shared abstraction is clearly needed

## Testing and validation

- Include automated testing appropriate for the architecture
- Use Playwright for end-to-end testing
- Include route-level screen capture / screenshot validation where practical
- Prioritise screenshot validation for major user-facing flows
- Validate not only APIs but also real UI states and route flows
- Tests should exercise realistic user journeys, not only isolated happy-path functions

## Delivery expectations

Work in this order:

1. Propose the architecture
2. Propose the schema
3. Critique the proposal for overengineering, weak spots, and unnecessary complexity
4. Refine the plan
5. Implement

Keep the output practical, not academic.

## Do not

- Do not build speculative features unless the app-specific prompt requires them
- Do not hide important business logic inside UI components
- Do not create one giant global CSS file
- Do not skip migrations or schema constraints because this is v1
- Do not optimise for a flashy demo at the expense of maintainability