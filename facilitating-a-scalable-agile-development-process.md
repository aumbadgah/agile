# Facilitating a scalable agile development process with technical integrations

## 1 Description

The goal of this document is to demostrate a way to recognize opportunities for implementation in an agile process.

## 2 Example business case

### 2.1 Goals

- Faster development cycle
- Scalable development process

### 2.2 Solutions

- Agile development process
- CI, CD automation

### 2.3 Added value

- Faster orientation
  - Familiar agile process
  - Reduced tech orientation requirement due to CI, CD automation
  - Reduced skillset requirement due to CI, CD automation
- Scalable development process
  - Asynchronic process support with Jira Kanban, GitLab merge requests and feature environments
  - Transparency and ease of communication with feature environments, GitLab process support and GitLab-Jira integration
- Reduced noise
  - Predictable process
  - Focus on relevant issues due to asynchronous process, CI, CD automation
  - More stable production due to predictable rollout process, reduced manual operation

### 2.4 Technologies

- Jira
- GitLab
- Docker
- Kubernetes

## 3 Diagram 1: Compact

```mermaid
gantt
dateFormat YYYY-MM-DD
axisFormat %Y-%m
title Facilitating a scalable agile development process. Diagram 1: Compact, Gantt chart
excludes weekdays 2022-06-06

section Process
Create task :done, des1, 2022-06-06, 2d
Refinement :done, des1, 2022-06-16, 2d
Planning :done, des1, 2022-06-26, 2d
Start work :done, des1, 2022-07-06, 2d
Submit to review :done, des1, 2022-07-16, 2d
Code review :done, des1, 2022-07-26, 2d
Product owner review :done, des1, 2022-07-26, 2d
Quality Assurance :done, des1, 2022-07-26, 2d
Approve :active, des1, 2022-08-06, 2d
User acceptance :active, des1, 2022-08-06, 2022-08-16
Release :done, des1, 2022-08-16, 2d

section Jira Kanban
Backlog :done, des1, 2022-06-06, 2022-06-26
Sprint backlog :done, des2, after des1, 2022-07-06
In progress :done, des3, after des2, 2022-07-16
Ready for review :done, des4, after des3, 2022-07-26
In review :active, des5, after des4, 2022-08-06
Ready for release :active, des6, after des5, 2022-08-16
Released :done, des7, after des6, 2022-08-26

section GitLab, Docker, Kubernetes
Create feature branch :done, des7, 2022-07-06, 2d
Automated feature builds CI :active, des7, 2022-07-06, 2022-08-06
Automated feature environment CI :active, des7, 2022-07-06, 2022-08-06
Continuous Deployments to feature environment :active, des7, 2022-07-06, 2022-08-06
Create merge request :done, des7, 2022-07-16, 2d
Merge request :done, des7, 2022-07-16, 2022-08-06
Require pass static analysis :done, des7, 2022-07-16, 2022-08-06
Require pass tests :done, des7, 2022-07-16, 2022-08-06
Require review approval(s) :done, des7, 2022-07-16, 2022-08-06
Forum for discussion :done, des7, 2022-07-16, 2022-08-06
Merge feature branch to main :active, des8, after des7, 2d
Continuous Deployment to staging environment :active, des8, after des7, 2022-08-26
Create release :done, des9, 2022-08-16, 2d
Continuous Deployment to production environment :done, des9, 2022-08-16, 2022-08-26

section Developer required skill set
Jira :active, des10, 2022-06-06, 2022-08-26
GitLab :active, des10, 2022-07-06, 2022-08-26
Git :active, des10, 2022-07-06, 2022-08-26
Docker Compose, Docker :done, des10, 2022-07-06, 2022-08-06
Application(s) :done, des10, 2022-07-06, 2022-08-06

section DevOps additional required skill set
GitLab :active, des10, 2022-07-06, 2022-08-26
Kubernetes :active, des10, 2022-07-06, 2022-08-26
Docker :done, des10, 2022-07-06, 2022-08-26
Application(s) :active, des10, 2022-07-06, 2022-08-26
```

### 3.1 Diagram 1 example implementation

Recognize a step in the process, `Approval`, to coincide with multiple changes to the state of our development technologies.

Define the step `Approve` in our process as the literal act of merging a new feature Merge Request into our main branch in our version control GitLab.

Create automatically triggered integrations into other technologies in our stack using GitLab CI:

- Remove the feature environment cloud resources (GitLab, Kubernetes, RDB, EC2)
- Set the status of the task on the board from In review to Ready for release (GitLab, Jira)
- Build and deploy a new release candidate to user acceptance environment (GitLab, Kubernetes)
- Notify stakeholders of changes to user acceptance environment (GitLab, Slack, email)

### 3.2 Diagram 1 skill sets

The skill set highlights in the diagram represent the highest relevance of a particular skill/technology in the task lifecycle.
Throughout the lifecycle they describe the technology focus change from product development tools to application development technologies and finally to operations technologies, and help in turn highlight potential process steps for automation.

## 4 Diagram 2: Extended

```mermaid
gantt
dateFormat YYYY-MM-DD
axisFormat %Y-%m
title Facilitating a scalable agile development process. Diagram 2: Extended, Gantt chart
excludes weekdays 2022-06-06

section Process
Create task :done, des1, 2022-06-06, 2d
Refinement :done, des1, 2022-06-16, 2d
Planning :done, des1, 2022-06-26, 2d
Start work :active, des1, 2022-07-06, 2d
Submit to review :active, des1, 2022-07-16, 2d
Code review :active, des1, 2022-07-26, 2d
Product owner review :active, des1, 2022-07-26, 2d
Approve review :active, des1, 2022-08-06, 2d
Quality Assurance :active, des1, 2022-08-06, 2022-08-16
Approve QA :active, des1, 2022-08-16, 2d
User acceptance :active, des1, 2022-08-16, 2022-08-26
Release :active, des1, 2022-08-26, 2d

section Jira Kanban
Backlog :done, des1, 2022-06-06, 2022-06-26
Sprint backlog :done, des2, after des1, 2022-07-06
In progress :done, des3, after des2, 2022-07-16
Ready for review :done, des4, after des3, 2022-07-26
In review :done, des5, after des4, 2022-08-06
Quality Assurance :done, des6, after des5, 2022-08-16
Ready for release :done, des7, after des6, 2022-08-26
Released :done, des11, 2022-08-26, 2022-09-06

section GitLab, Docker, Kubernetes
Create feature branch :active, des7, 2022-07-06, 2d
Automated feature builds CI :active, des7, 2022-07-06, 2022-08-06
Automated tests CI :active, des7, 2022-07-06, 2022-08-06
Continuous Deployments to feature environment :active, des7, 2022-07-06, 2022-08-06
Create merge request :active, des7, 2022-07-16, 2d
Merge request :active, des7, 2022-07-16, 2022-08-06
Require pass static analysis :done, des7, 2022-07-16, 2022-08-06
Require pass tests :done, des7, 2022-07-16, 2022-08-06
Require review approval(s) :done, des7, 2022-07-16, 2022-08-06
Forum for discussion :done, des7, 2022-07-16, 2022-08-06
Merge feature branch to dev :active, des8, after des7, 2d
Continuous Deployment to development environment :active, des8, after des7, 2022-09-06
Merge dev to main :active, des9, 2022-08-16, 2d
Continuous Deployment to staging environment :active, des9, 2022-08-16, 2022-09-06
Create release :active, des9, 2022-08-26, 2d
Continuous Deployment to production environment :active, des9, 2022-08-26, 2022-09-06

section Developer required skill set
Jira :active, des10, 2022-06-06, 2022-09-06
GitLab :active, des10, 2022-07-06, 2022-09-06
Git :active, des10, 2022-07-06, 2022-09-06
Docker Compose, Docker :active, des10, 2022-07-06, 2022-08-06
Application(s) :active, des10, 2022-07-06, 2022-08-06

section DevOps additional required skill set
GitLab :active, des10, 2022-07-06, 2022-09-06
Kubernetes :active, des10, 2022-07-06, 2022-09-06
Docker :active, des10, 2022-07-06, 2022-09-06
Application(s) :active, des10, 2022-07-06, 2022-09-06
```

## 5 Technology choices

Continued availability and stability of integrations between technologies are key for long term sustainability of an implemented process.
Every implementation will require maintenance, so the further a process is implemented, the more value low maintenance, easily portable options will produce.

In other words

- Choose technologies that are widely supported and offer standardized integrations.
- Avoid customizations in favor of suggested best practices, standards and conventions.
