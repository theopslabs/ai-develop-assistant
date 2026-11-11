# ai-develop-assistant
## 1. Prepare the project workspace
Create a project directory and open it using Coding Agent.

Suggested project structure:

```bash
company-portfolio-platform/
├── apps/
│   ├── web/
│   └── cms/
├── packages/
├── infrastructure/
├── docs/
├── .github/
│   └── workflows/
├── README.md
└── AGENTS.md
```
You don't need to create all these folders manually. Coding Agent can create them during the foundation phase.

## Recommended development approach
Development sequence           
1. Project planning and architecture
2. Repository and development foundation
3. Strapi CMS and database
4. Admin portal and RBAC
5. Next.js design system
6. Public website development
7. CMS and frontend integration
8. SEO and performance
9. Security and testing
10. CI/CD and production deployment

## 2. Phase 1 — Project planning and architecture
First, ask Coding Agent to understand the requirements and prepare the project documentation. Do not allow it to start implementing everything immediately.

```text
# Phase 1: Company Portfolio Platform — Architecture Planning

Act as a Senior Software Architect and Technical Lead.

I want to develop a dynamic company portfolio website for a Software Development Company.

## Project Requirements

- Frontend: Next.js with App Router
- CMS: Strapi 5
- Database: PostgreSQL
- UI: Tailwind CSS and shadcn/ui
- Media Storage: Amazon S3
- Hosting: Vercel for Next.js
- CMS Hosting: Managed container hosting
- API: Strapi REST API
- Source Control: GitHub
- CI/CD: GitHub Actions
- Website Language: English
- Admin Users: 3–5

## Website Modules

1. Homepage
2. About Us
3. Services
4. Projects / Portfolio
5. Blog / News
6. Our Team
7. Clients & Partners
8. Testimonials
9. Contact Us

## Admin Portal Modules

1. Dashboard
2. Homepage Management
3. About Us Management
4. Services Management
5. Projects Management
6. Blog Management
7. Media Library
8. Team Management
9. Client Management
10. SEO Management
11. User Management
12. Role-Based Access Control
13. Audit Logs
14. Website Settings

## Architecture Requirements

- Use a monorepo architecture.
- Separate frontend and CMS applications.
- Use structured Strapi content types.
- Support Dynamic Zones for configurable page sections.
- Support Draft & Publish.
- Implement role-based access control.
- Use webhook-based Next.js cache revalidation.
- Support staging and production environments.
- Follow security and scalability best practices.

## Your Tasks

1. Analyze the requirements.
2. Propose the complete system architecture.
3. Design the logical database model and entity relationships.
4. Define Strapi content types and reusable components.
5. Define frontend page architecture.
6. Define the API integration strategy.
7. Define deployment architecture.
8. Identify security risks and mitigations.
9. Create a development roadmap.

## Documentation Deliverables

Create these documents inside the docs/ directory:

- architecture.md
- database-design.md
- cms-content-model.md
- frontend-architecture.md
- deployment-architecture.md
- development-roadmap.md

IMPORTANT:
- Do not write application code yet.
- Do not commit or push any changes.
- Do not make infrastructure changes.
- Explain important architectural decisions and trade-offs.
- Identify any missing requirements before proceeding.
```
Expected result: Claude Code creates the architecture documentation and identifies missing decisions before implementation.

Review the documentation before continuing.

## 3. Phase 2 — Repository and development foundation
Once you approve the architecture, establish the monorepo.

```text
# Phase 2: Initialize the Project Foundation

Act as a Senior Full-Stack Engineer.

Based on the approved architecture documentation in docs/, initialize the company portfolio monorepo.

## Requirements

Repository structure:

company-portfolio-platform/
├── apps/
│   ├── web/
│   └── cms/
├── packages/
├── docs/
├── infrastructure/
├── .github/workflows/
├── CLAUDE.md
└── README.md

## Frontend

Initialize:
- Next.js using App Router.
- TypeScript.
- Tailwind CSS.
- shadcn/ui.
- ESLint.
- Prettier.

## CMS

Initialize:
- Strapi 5.
- TypeScript.
- PostgreSQL integration.
- Environment-based configuration.

## Engineering Standards

- Use stable, mutually compatible dependency versions.
- Use strict TypeScript settings.
- Keep frontend and CMS dependencies isolated.
- Add appropriate .gitignore files.
- Provide .env.example files without real credentials.
- Document local development setup.
- Use consistent naming conventions.
- Avoid unnecessary dependencies.

## Validation

- Verify the frontend development server.
- Verify the Strapi development server.
- Verify PostgreSQL connectivity.
- Verify linting and TypeScript checks.
- Document startup commands.

Do not commit or push any changes.
Do not deploy to production.
Do not use real production credentials.

At the end, provide a summary of files created, dependencies installed, validation results, and remaining tasks.
```
Expected result: Both applications can run independently in your local environment.

## 4. Phase 3 — Strapi CMS and database development
This is the most important backend phase.

Ask Claude Code to build the content models before working on the public website.
```text
# Phase 3: Develop Strapi CMS and Database Models

Act as a Senior Strapi 5 Backend Developer and Database Architect.

Refer to:
- docs/architecture.md
- docs/database-design.md
- docs/cms-content-model.md

Implement the complete Strapi CMS content architecture.

## 1. Single Types

Create:

- Homepage
- About Page
- Contact Page
- Global Website Settings

## 2. Collection Types

Create:

- Service
- Project
- Blog Post
- Blog Category
- Blog Tag
- Team Member
- Client
- Testimonial

## 3. Reusable Components

Create reusable components for:

- SEO metadata
- Hero section
- Call-to-action
- Statistics
- Feature cards
- Social links
- Image and text sections
- Technology stacks
- Project information
- Contact information

## 4. Dynamic Zones

Implement configurable homepage sections using Strapi Dynamic Zones.

Allow content managers to add, remove, and reorder supported sections.

Do not implement arbitrary frontend code execution or unrestricted HTML injection.

## 5. Relationships

Implement the appropriate relationships:

- Blog Post → Category
- Blog Post → Tags
- Blog Post → Author
- Project → Client
- Project → Services
- Project → Technologies
- Project → Project Images
- Testimonial → Client

## 6. Content Requirements

Every appropriate collection should support:

- Title
- Slug
- Description
- Featured image
- Publication status
- Created timestamp
- Updated timestamp
- SEO metadata

Use Draft & Publish where appropriate.

## 7. Media Library

Configure Strapi Upload Provider for Amazon S3.

Support:
- Image uploads
- Image metadata
- File validation
- Appropriate file size limits
- Public asset delivery
- Environment-specific storage configuration

## 8. Database

Configure PostgreSQL using environment variables.

Ensure:
- Proper relationships
- Database indexes for frequently queried fields
- Unique slugs where appropriate
- Database backup considerations
- No hardcoded database credentials

## 9. API

Configure REST API endpoints and content permissions.

Public visitors should only access published content.

Admin operations must require appropriate authorization.

## 10. Testing

Test:
- Content creation
- Content updates
- Publishing
- Unpublishing
- Relationships
- API responses
- Media uploads
- Database persistence

At the end, document all content types, fields, relationships, API endpoints, and configuration decisions.

Do not commit or push changes.
Do not deploy to production.
```
Expected result: A working Strapi backend with all required content types and database relationships.

## 5. Phase 4 — Admin portal and RBAC
Strapi already provides an admin interface. Your goal is to configure it properly rather than unnecessarily rebuilding the entire CMS dashboard.
```text
# Phase 4: Configure Strapi Admin Portal and RBAC

Act as a Senior Strapi CMS Administrator and Application Security Engineer.

Configure the Strapi admin portal for a company portfolio website managed by 3–5 administrators.

## Admin Roles

Create the following logical roles:

### 1. Super Admin
- Full administrative access.
- Manage admin users.
- Manage roles and permissions.
- Manage all website content.
- Configure CMS settings.

### 2. Content Manager
- Create and update all website content.
- Review content.
- Publish and unpublish content.
- Manage projects and blog posts.

### 3. Content Editor
- Create and update assigned content.
- Upload media.
- Save drafts.
- Cannot manage users or system settings.
- Cannot publish content unless explicitly authorized.

### 4. SEO Manager
- Manage SEO metadata.
- Manage page titles and descriptions.
- Manage social sharing metadata.
- Review SEO content.

### 5. Media Manager
- Upload and organize media.
- Update media metadata.
- Manage approved media assets.

## Requirements

1. Configure Strapi Admin RBAC.
2. Apply least-privilege permissions.
3. Restrict access to sensitive collections.
4. Separate admin permissions from public API permissions.
5. Ensure public APIs cannot access draft content.
6. Configure secure authentication.
7. Enable MFA where supported.
8. Review admin session and password security.
9. Document role-permission mappings.

## Publishing Workflow

Configure:
- Draft creation.
- Content review.
- Publishing.
- Unpublishing.
- Content revision history.

Use supported Strapi features or a suitable workflow implementation for approval requirements.

## Audit and Security

Provide a mechanism to track:
- Admin login activity.
- Content creation.
- Content updates.
- Publishing activity.
- Permission changes.

Do not assume built-in content revision history is a complete security audit log.

## Testing

Create test scenarios for each role.

Verify that users cannot perform operations outside their permissions.

Do not create production admin accounts or passwords.
Do not commit or push changes.

Document the final permissions matrix.
```
Expected result: A secure admin portal with clearly separated responsibilities.

## 6. Phase 5 — Next.js frontend design system
Now start the public website.

I recommend completing the design system before developing all pages.
```text
# Phase 5: Build Next.js Design System

Act as a Senior Frontend Architect and UI/UX Designer.

Develop the frontend design system for the company portfolio website.

Technology:
- Next.js App Router
- TypeScript
- Tailwind CSS
- shadcn/ui

## Design Direction

Create a modern, professional, premium software development company website.

Visual characteristics:
- Clean corporate design.
- Technology-oriented appearance.
- Professional typography.
- Consistent spacing.
- High-quality imagery.
- Subtle animations.
- Accessible color contrast.
- Responsive layouts.

Avoid making the website look like an admin dashboard or a generic template.

## Design System

Create:
1. Color palette.
2. Typography system.
3. Spacing system.
4. Responsive breakpoints.
5. Button variants.
6. Card components.
7. Navigation components.
8. Footer components.
9. Form components.
10. Loading and error states.

## Shared Components

Implement reusable components for:

- Header
- Navigation
- Mobile navigation
- Footer
- Hero
- Section heading
- Service card
- Project card
- Blog card
- Testimonial card
- Team card
- CTA section
- Breadcrumb
- Pagination
- Contact form
- Loading skeleton

## Responsive Requirements

Support:
- Desktop
- Tablet
- Mobile

## Accessibility

Follow WCAG 2.2 AA principles where practical.

Ensure:
- Keyboard navigation.
- Semantic HTML.
- Appropriate image alt text.
- Accessible form labels.
- Sufficient color contrast.
- Visible focus states.

## Instructions

Create the design system before implementing the complete website.

Use reusable components and avoid duplicated styling.

Do not introduce unnecessary UI libraries.

Do not commit or push changes.

Provide screenshots or visual previews where available and document the design decisions.
```
Expected result: A consistent visual system that can be reused across all website pages.

## 7. Phase 6 — Public website development
Once the design system is ready, develop the website page by page.

I recommend using one prompt per major group of pages so Claude Code can focus on each implementation.
```text
# Phase 6: Develop the Company Portfolio Website

Act as a Senior Next.js Developer.

Implement the public-facing website using the approved design system.

Technology:
- Next.js App Router
- TypeScript
- Tailwind CSS
- shadcn/ui
- Strapi 5 REST API

## Pages

### Homepage
- Hero section.
- Company introduction.
- Services overview.
- Featured projects.
- Technology expertise.
- Client logos.
- Testimonials.
- Latest blog articles.
- Contact CTA.

### About Us
- Company profile.
- Mission and vision.
- Core values.
- Company history.
- Leadership information.

### Services
- Service listing.
- Service details.
- Related projects.
- CTA.

### Projects
- Project listing.
- Project filtering.
- Project details.
- Project images.
- Technologies used.
- Business outcomes.

### Blog / News
- Blog listing.
- Categories.
- Search.
- Pagination.
- Article details.
- Related articles.
- Author information.

### Our Team
- Team member listing.
- Profile information.

### Clients and Partners
- Client logos.
- Client information.
- Testimonials.

### Contact Us
- Contact form.
- Company information.
- Office address.
- Social links.

## Implementation Requirements

1. Build reusable page components.
2. Retrieve content dynamically from Strapi.
3. Never hardcode CMS-managed content in frontend components.
4. Support empty content and loading states.
5. Implement appropriate error handling.
6. Use Next.js Server Components by default.
7. Use Client Components only where interactivity requires them.
8. Optimize images.
9. Implement responsive layouts.
10. Ensure published content is displayed correctly.

## Frontend Quality

- Strict TypeScript.
- Consistent component structure.
- No unnecessary dependencies.
- No duplicated components.
- No hardcoded secrets.
- Semantic HTML.
- Accessible UI.

## Validation

Test every page using actual Strapi content.

Do not use fake data in production-facing content.

Do not commit or push changes.

Provide a list of completed pages and outstanding issues.
```
Expected result: A fully functional public website powered by Strapi content.

## 8. Phase 7 — Strapi and Next.js integration
This phase is particularly important because the frontend and CMS are separate applications.
```text
# Phase 7: Integrate Next.js with Strapi 5

Act as a Senior Full-Stack Integration Engineer.

Integrate the Next.js frontend with the Strapi 5 backend.

## API Integration

Implement a centralized Strapi API client.

Requirements:

- Environment-based CMS URL.
- Secure API token handling.
- REST API integration.
- Pagination.
- Filtering.
- Sorting.
- Population of required relationships.
- Error handling.
- Type-safe API responses.

## Content Retrieval

Implement API integrations for:

- Homepage
- About
- Services
- Projects
- Blog Posts
- Categories
- Team Members
- Clients
- Testimonials
- Site Settings

Only retrieve published content for public routes.

## Cache Management

Implement an appropriate Next.js caching strategy.

Use:
- Static generation where suitable.
- ISR for content-heavy pages.
- Dynamic rendering where necessary.
- Cache tags for related content.

## Webhook Integration

Configure Strapi webhooks to notify Next.js when content is:

- Published.
- Updated.
- Unpublished.
- Deleted.

Create a protected Next.js webhook endpoint.

Requirements:
- Verify webhook authenticity using a secret or signature.
- Validate event payloads.
- Revalidate affected paths or cache tags.
- Prevent unauthorized cache invalidation.
- Log webhook failures.
- Handle repeated webhook events safely.

## Preview Mode

Implement secure draft preview functionality.

Ensure draft content is never accessible through public endpoints without proper authorization.

## Testing

Test:
1. Publishing a new project.
2. Updating an existing project.
3. Publishing a blog article.
4. Updating homepage content.
5. Unpublishing an article.
6. Webhook delivery failure.
7. Cache invalidation.

Document the API endpoints and caching strategy.

Do not expose private API tokens to browser-side code.
Do not commit or push changes.
```
Expected result: When an administrator publishes content in Strapi, the public website updates without a manual deployment.

## 9. Phase 8 — SEO and performance optimization
```text
# Phase 8: SEO and Performance Optimization

Act as a Technical SEO Engineer and Next.js Performance Engineer.

Optimize the company portfolio website.

## SEO Requirements

Implement:
- Dynamic page titles.
- Meta descriptions.
- Canonical URLs.
- Open Graph metadata.
- Twitter/X card metadata.
- XML sitemap.
- Robots.txt.
- Breadcrumb structured data.
- Organization structured data.
- Article structured data.
- Proper heading hierarchy.
- Image alt attributes.

SEO metadata must be managed through Strapi.

## Performance

Implement:
- Next.js image optimization.
- Responsive images.
- Lazy loading.
- Font optimization.
- Appropriate caching.
- Code splitting.
- Avoid unnecessary client-side JavaScript.
- Avoid layout shifts.

## Target Metrics

Aim for:
- Lighthouse Performance: 90+
- Accessibility: 90+
- SEO: 90+
- Best Practices: 90+

## Validation

Test:
- Homepage.
- Service detail.
- Project detail.
- Blog detail.
- Contact page.

Use Lighthouse and PageSpeed Insights.

Identify and fix significant performance issues.

Document the results and remaining improvements.

Do not commit or push changes.
```
## 10. Phase 9 — Security and testing
Before production deployment, ask Coding Agent to perform a dedicated security and quality review.
```text
# Phase 9: Security Audit and Application Testing

Act as a Senior Application Security Engineer and QA Engineer.

Perform a security and quality audit of the company portfolio platform.

## 1. Authentication and Authorization

Review:
- Strapi admin authentication.
- Admin RBAC.
- Public API permissions.
- API token permissions.
- Draft content access.
- Preview authentication.
- Contact form submission permissions.

## 2. Application Security

Check:
- XSS.
- CSRF where applicable.
- SQL injection risks.
- Input validation.
- File upload validation.
- Rate limiting.
- Secret exposure.
- Authentication weaknesses.
- Insecure API endpoints.
- Dependency vulnerabilities.
- Security headers.

## 3. Database Security

Review:
- Database access restrictions.
- Database credentials.
- Backup configuration.
- Database connection security.
- Data exposure risks.

## 4. Functional Testing

Test:
- Homepage content.
- Services.
- Projects.
- Blog.
- Search and filtering.
- Pagination.
- Contact form.
- CMS publishing.
- CMS unpublishing.
- Media uploads.
- Admin permissions.
- SEO metadata.

## 5. Automated Testing

Use appropriate:
- Unit tests.
- Integration tests.
- API tests.
- End-to-end tests.

Use Playwright for important user journeys.

## 6. Security Reporting

Produce:

docs/security-audit.md
docs/testing-report.md

Classify findings as:
- Critical
- High
- Medium
- Low

Fix critical and high-severity issues before production.

Do not expose secrets in reports.

Do not commit or push changes.

Provide test results and remaining risks.
```
## 11. Phase 10 — CI/CD and production deployment
For your DevOps background, I recommend implementing independent pipelines for Next.js and Strapi.
```text
# Phase 10: Production Deployment and CI/CD

Act as a Senior DevOps Engineer and Cloud Architect.

Prepare the company portfolio platform for production deployment.

## Hosting Architecture

Frontend:
- Next.js hosted on Vercel.

Backend:
- Strapi 5 hosted on a persistent managed container platform.
- PostgreSQL hosted using managed database services.
- Amazon S3 for media storage.

Domains:
- www.company.com
- cms.company.com

## GitHub Actions

Create independent workflows for:

### Frontend Pipeline

1. Install dependencies.
2. Run linting.
3. Run TypeScript checks.
4. Run unit tests.
5. Build Next.js.
6. Validate the production build.

Use Vercel's GitHub integration for preview and production deployments, or document a consistent GitHub Actions-based deployment alternative.

### CMS Pipeline

1. Install dependencies.
2. Run linting.
3. Run TypeScript checks.
4. Run tests.
5. Build Strapi.
6. Build the container image.
7. Run security scanning.
8. Deploy to the managed hosting environment.

## Environments

Configure:
- Development
- Staging
- Production

Ensure each environment has independent:
- Database configuration.
- API tokens.
- Secrets.
- Media configuration.
- Webhook configuration.

## Production Requirements

- HTTPS.
- Custom domains.
- Database backups.
- Database restore procedure.
- Monitoring.
- Error tracking.
- Application logs.
- Health checks.
- Rollback strategy.
- Deployment documentation.

## Infrastructure

Document the deployment architecture and resource requirements.

Do not create expensive cloud resources without explicit approval.

Do not modify existing production infrastructure.

Do not commit or push any changes.

## Deliverables

Create:
- docs/production-deployment.md
- docs/cicd-architecture.md
- docs/backup-and-restore.md
- docs/operations-runbook.md

Provide a production readiness report and outstanding tasks.
```

## 12. Create a permanent AGENTS.md project instruction
This is something I strongly recommend.

Coding Agent uses AGENTS.md as project-level guidance. It helps maintain consistent architectural decisions across different development sessions.

After the architecture is approved, give Coding Agent this prompt:
```text
# Create Project-Level AGENTS.md

Create a comprehensive AGENTS.md file at the root of this repository.

The file must establish permanent development instructions for the company portfolio platform.

## Project Architecture

- Monorepo.
- Next.js App Router frontend.
- Strapi 5 backend.
- PostgreSQL database.
- Tailwind CSS.
- shadcn/ui.
- Amazon S3 media storage.
- Vercel frontend hosting.

## Development Standards

- Use TypeScript.
- Follow strict TypeScript practices.
- Use reusable components.
- Follow separation of concerns.
- Use appropriate server/client component boundaries.
- Use centralized API integration.
- Follow secure coding practices.
- Avoid unnecessary dependencies.
- Keep documentation updated.

## Strapi Standards

- Use Strapi 5 conventions.
- Use structured content types.
- Use reusable components.
- Use Dynamic Zones appropriately.
- Use Draft & Publish.
- Apply least-privilege permissions.
- Keep API tokens secure.

## Frontend Standards

- Use Next.js App Router.
- Prefer Server Components.
- Use Client Components only when needed.
- Implement responsive design.
- Follow accessibility principles.
- Optimize images and metadata.
- Do not hardcode CMS-managed content.

## DevOps Standards

- Maintain separate environments.
- Use environment variables for configuration.
- Never commit secrets.
- Validate builds before deployment.
- Document deployment procedures.
- Keep frontend and CMS pipelines independent.

## Git Safety

IMPORTANT:
- Never execute git commit.
- Never execute git push.
- Never create commits automatically.
- Never push changes to remote repositories.
- Never force-push.
- Do not modify Git history.
- Leave all changes available for manual review.

## Working Method

Before implementing a task:

1. Inspect the existing project.
2. Read the relevant documentation.
3. Understand existing architecture.
4. Explain the proposed changes.
5. Identify potential breaking changes.

After implementation:

1. Run appropriate tests.
2. Run linting.
3. Run TypeScript checks.
4. Verify build results.
5. Summarize modified files.
6. Document outstanding issues.

Do not overwrite existing working implementations without reviewing them first.

Always follow these project instructions.
```
This is particularly useful when you continue development over multiple days.

## 13. How to work with Claude Code effectively
I recommend following this workflow for every phase.

```text
Your development cycle
1. Ask Claude to analyze
   
   Give it the phase prompt and ask it to inspect the current repository.
2. Review its implementation plan
   
   Check which files it intends to create or modify.
3. Approve implementation
   
   Let Claude implement only the approved scope.
4. Run validation
   
   Ask it to run tests, linting, type checking and builds.
5. Review changes
   
   Inspect the actual code and test results yourself.
6. Update documentation
   
   Ask Claude to update the architecture and development documentation.
7. Move to the next phase
   
   Proceed only after the current phase passes its acceptance criteria.
```

Useful prompts during development
These are reusable prompts you can give Claude Code whenever necessary.

### A. Before changing existing code
```text
Before making any changes, inspect the existing implementation and explain:

1. What currently exists.
2. Which files need modification.
3. Why those changes are necessary.
4. Whether any existing functionality could break.
5. What tests should be executed.

Do not modify files until I approve the implementation plan.
```
### B. When Code generates errors
```text
Analyze the reported error carefully.

Do not immediately rewrite the implementation.

1. Identify the root cause.
2. Inspect the relevant configuration and source files.
3. Explain why the error occurs.
4. Propose the smallest safe fix.
5. Implement the fix after confirming the approach.
6. Run the relevant tests and verify the result.

Do not introduce unnecessary dependencies or unrelated changes.
```
### C. Code review
```text
Perform a senior-level code review of the current implementation.

Review:

- Architecture and separation of concerns.
- TypeScript quality.
- Security.
- Performance.
- Error handling.
- Database design.
- API integration.
- Accessibility.
- Maintainability.

Identify issues by severity and provide recommended improvements.

Do not modify files during this review. Do not commit or push anything.
```
### D. Before completing each phase
```text
Perform a phase completion review.

Check the implementation against the original project requirements and acceptance criteria.

Provide:

1. Completed features.
2. Incomplete features.
3. Files created or modified.
4. Test execution results.
5. Build results.
6. Security concerns.
7. Technical debt.
8. Remaining blockers.

Do not claim a feature is complete unless it has been verified.

Do not commit or push changes.
```
## 14. Recommended development order and checkpoints
Here is the sequence I would personally follow for this project.
Step	Task	Completion checkpoint
1	Architecture planning	Documents approved
2	Monorepo foundation	Both applications run
3	Strapi content models	All content types work
4	Admin RBAC	Permissions tested
5	Frontend design system	UI approved
6	Public website	All pages implemented
7	API integration	Dynamic content works
8	SEO and performance	SEO and Lighthouse validated
9	Security testing	High-risk issues resolved
10	CI/CD and deployment	Production readiness verified

## My additional recommendation: Don't let Claude Code do everything in one session
For example, instead of saying:
> Build the entire company portfolio website.
Use smaller tasks:
- Build homepage hero section.
- Integrate homepage content from Strapi.
- Build service listing.
- Integrate service details.
- Build project listing.
- Implement project filtering.
- Build blog listing.
- Implement article details.
- Implement SEO metadata.
