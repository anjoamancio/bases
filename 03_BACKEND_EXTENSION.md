03_BACKEND_EXTENSION.md

Backend Discovery Extension

Apply this extension when the current repository contains a backend service, API, application server, worker, or persistence layer.

The Core Repository Discovery Prompt remains authoritative. This extension adds backend-specific requirements.

Backend Focus Areas

Give special attention to:

Application entry points

Route registration

Controllers or handlers

Services

Domain logic

Repositories

Data-access layers

Database entities

Migrations

Validation

Serialization

Authentication

Authorization

Tenant isolation

Country or regional scoping

Logging

Audit logging

Caching

Queues

Scheduled jobs

File storage

External integrations

Rate limiting

API documentation

Tests

Deployment configuration

Endpoint Discovery

For every relevant endpoint, capture:

Owner module

Method

Route

Purpose

Authentication

Authorization

Path parameters

Query parameters

Request schema

Response schema

Validation

Error codes

Pagination

Filtering

Sorting

Idempotency

Caching

Rate limiting

Side effects

Audit behavior

Events or jobs

Consumer, if known

Evidence

Confidence

Add endpoints to the YAML contracts collection.

Domain and Service Logic

Document:

Domain boundaries

Service responsibilities

Transaction boundaries

Business rules

Validation layers

Error translation

Retry logic

Integration boundaries

Side effects

Event publication

Audit requirements

Do not treat transport handlers as the sole business-logic source when services or domain modules exist.

Data and Migrations

Use the Core entity template.

Additionally document:

Migration owner

Migration ordering

Seed data

Backfills

Soft deletion

Retention

Index strategy

Transaction behavior

Concurrency controls

Tenant isolation

Country or regional scoping

Compatibility risks

Add entities to the YAML entities collection.

Authentication and Authorization

Identify:

Authentication middleware

Token verification

Session handling

Claims

Role and permission checks

Resource ownership checks

Tenant isolation

Country or regional restrictions

Administrative overrides

Audit logging

Unauthorized and forbidden error contracts

Document server-side enforcement locations.

Workers and Asynchronous Processing

Where applicable, document:

Queues

Topics

Job types

Payload schemas

Producers

Consumers

Retry policy

Dead-letter behavior

Idempotency

Scheduling

Concurrency

Observability

Failure recovery

Represent these as contracts in YAML.

Backend Testing

Identify:

Unit tests

Service tests

API tests

Database tests

Migration tests

Contract tests

Integration tests

Queue tests

Security tests

Performance tests

The implementation outline should include tests for:

Validation

Authentication

Authorization

Ownership

Tenant isolation

Country or regional scoping

Business rules

Database constraints

Error contracts

Pagination

Filtering

Sorting

Idempotency

Side effects

Backend Output Emphasis

The Markdown report must include:

Endpoint inventory

Service and domain map

Entity and relationship map

Authentication and authorization map

External integration map

Queue or worker map

Migration risks

The YAML must populate, where applicable:

contracts

entities

permissions

external_dependencies

architecture.runtime_services

implementation_outline

04_MULTI_REPO_EXTENSION.md

Multi-Repository Discovery Extension

Apply this extension when the application is split across separate repositories or services.

Run discovery independently in each repository.

Do not combine repository findings during discovery. Combination occurs only during synthesis.

Repository Boundary Rules

For every feature or capability, identify:

Current repository responsibility

Responsibility belonging to another repository

Shared contract

External dependency

Unknown ownership

Use:

Capability

Current Repository

Other Repository

Shared Contract

Confidence

Cross-Repository Contracts

Identify:

HTTP APIs

GraphQL operations

RPC calls

WebSocket messages

Events

Queue payloads

Webhooks

Authentication claims

Shared types

Generated SDKs

OpenAPI specifications

GraphQL schemas

Environment variables

Feature flags

File formats

Storage conventions

Error formats

Pagination formats

Date formats

Identifier formats

Permission names

Tenant context

Country or regional context

Versioning rules

For each contract, use the Core Standard Contract Template.

Other Repository Dependencies

Create a section named:

Dependencies on Other Repositories

For every dependency include:

Repository or service name

Suspected responsibility

Evidence

Required interface

Data exchanged

Information needed

Risk if incorrect

Validation method

Blocking status

Add dependencies to YAML external_dependencies.

Unknowns for Synthesis

Explicitly identify questions such as:

Does the backend endpoint already exist?

Is the frontend using the current API version?

Are types generated or handwritten?

Which repository owns schemas?

Which repository owns permission definitions?

Which repository owns migrations?

Which repository owns feature flags?

Which service owns notifications?

Which service owns file storage?

Which repository owns tenant or country scoping?

What deployment order is required?

What backward-compatibility guarantees exist?

Add these to YAML unknowns.

Repository-Specific Output

The discovery outputs must not claim to be the final implementation specification.

They must state:

This repository discovery must be reconciled with the discovery outputs from all related repositories before implementation begins.

The final synthesis agent will use both the Markdown and YAML outputs.