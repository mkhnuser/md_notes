# OpenTelemetry

## Overview

OpenTelemetry allows one to examine the state of your system.
A system has to emit telemetry in order to be observed.

## Types of Telemetry

There is User Telemetry and Performance Telemetry.

## Telemetry Signals

Signals are particular types of telemetry.
System Metrics is one form of signal, event logs is another form of signal.
You need different kinds of signals to understand your system as a whole.

### Two Signal Components

Instrumentation is a piece of software which emits a signal;
transmission system transmits a signal to an analysis tool, where an observing occurs.

## The Three Pillars of Observability

The Three pillars of observability are logs, metrics and traces.

### The Usual Problem with the Three Pillars

For historical reasons, each pillar has been built in silos:
logging is completely separate from metrics, metrics from tracing, and so on.
Therefore, when a transaction happens, one needs to correlate the three pillars to
understand what's going on, which is extremely hard and time-consuming.

https://en.wikipedia.org/wiki/Information_silo

## Traces

Trace is a group of spans with the same trace_id.
One Trace is composed of multiple spans.
Traces allow you to examine transactional interaction with your system.

## Metrics

Metrics succinctly show you the system state and resource utilization.

## Logs

OpenTelemetry associates logs with the underlying context, which does not
make them isolated.

## Context

Context propagates information between logical parts of your system.
Context holds one or more propagators.

## Propagators

Propagators send values from one process to the next.

## Attributes

Be careful with cardinality explosion when you add attributes to metrics.

Source: Learning OpenTelemetry, chapter 3 - OpenTelemetry Overview, Attributes and Resources.

## Resources

The difference between Attribute and Resource is that the latter never changes.

## Telemetry Schemas

Telemetry Schema allows one to change how telemetry is analyzed and collected
in a centralized manner.

https://opentelemetry.io/docs/specs/otel/schemas/

## Semantic Conventions

Use them to identify resources which you monitor.
