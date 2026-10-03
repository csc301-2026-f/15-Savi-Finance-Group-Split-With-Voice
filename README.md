# Savi Finance — Group Split with Voice

> D1 foundation. Replace `[TODO]` items as the project becomes defined.

## Project

This project is a proposed application for recording and splitting shared group expenses, with voice input as a possible feature.

## Deliverable 1

- [Planning document](deliverables/D1/planning.md)
- [Interactive mockup](deliverables/D1/mockup.html)
- Team information: `deliverables/team/`

## Confirmed Course and Meeting Context

- Official CSC301 group number: **15**. Team name in the tutorial schedule: **Team 12**.
- Deliverable 1 is due **Friday, October 2, 2026 at 11:59pm Toronto time**. [Quercus assignment](https://q.utoronto.ca/courses/441425/assignments/1794225).
- Tutorial: **Thursdays, 7:00-7:30pm Toronto time**, with mentor TA **Rayan El Ghazzi**. D1 Demo Day is **Thursday, October 1, 2026**. [Tutorial schedule](https://q.utoronto.ca/courses/441425/pages/tutorial-schedule).
- Recurring partner meeting: **Wednesdays, 6:00-6:20pm Toronto time**, on [Google Meet](https://meet.google.com/ogv-qkay-sxa), organized by **ralphpalxyz@gmail.com**.
- Mentor TA contact: **rayan.el.ghazzi@mail.utoronto.ca**. [Course syllabus](https://q.utoronto.ca/courses/441425/assignments/syllabus).

## Task Management

The team will use **Jira for ticketing and task distribution and Slack for asynchronous communication**. We have been granted access to Savi Finance's internal platforms, and will use those for the duration of the project. 

## Access and Use

There is no deployed application yet. Open `deliverables/D1/mockup.html` in a browser to view the D1 prototype.

## Development Requirements

The implementation stack and setup instructions are still being decided. **[TODO: add requirements and local setup commands once selected]**.

## External Dependencies

Our Group Split feature will depend on Savi's existing application stack, internal APIs, and third-party services.

### Application and Framework Dependencies
- **React Native** — used to build the Savi mobile application.
- **Expo / EAS** — used for local mobile development and mobile builds/deployment.
- **Go + Bazel** — used for Savi's backend services and build system.
- **MongoDB** — Savi's primary database.

### Internal APIs and Services
- **`sf1/api`** — Savi's main backend API, which the mobile application uses to communicate with backend functionality.
- **Existing transaction and receipt services** — may be used when creating splits from existing Savi transactions or receipt data.
- **Existing voice-agent / MCP infrastructure** — may be used for voice-based follow-ups and interactions if this portion of the project is implemented.

### Third-Party Services and APIs
- **Plaid** — Savi's existing banking data provider and may be relevant for transaction-based splitting.
- **OpenAI** — used by Savi for AI-powered functionality and may support voice/AI features.
- **AWS services** — Savi uses AWS services such as S3 for storage and infrastructure.
- **GitHub Actions** — used as part of Savi's CI/CD process.

The exact APIs and third-party services required specifically by Group Split have not yet been finalized and will be confirmed during technical design and implementation.

## GitHub Workflow

The team will use feature branches and pull requests. **Regarding naming, review, merge and naming conventions, we will exclusively follow Savi Finance's established practices as we are directly working on the company's monorepo**.

## License

Our contributions will follow Savi Finance's existing licensing and confidentiality requirements, since we are developing directly within their privately-owned codebase. We will not apply a separate open-source license unless the partner requests.

The code is intended for use within Savi's product and will not be publicly redistributed without permission.
