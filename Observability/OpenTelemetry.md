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

## Metrics

Metrics succinctly show you the system state and resource utilization.

## The Three Pillars of Observability

The Three pillars of observability are logs, metrics and (distributed) traces.

### The Usual Problem with the Three Pillars

For historical reasons, each pillar has been built in silos:
logging is completely separate from metrics, metrics from tracing, and so on.
Therefore, when a transaction happens, one needs to correlate the three pillars to
understand what's going on, which is extremely hard and time-consuming.

https://en.wikipedia.org/wiki/Information_silo

## Spans

Trace is a group of spans with the same trace_id.
One Trace is composed of multiple spans.

## Semantic Conventions

Use them to identify resources which you monitor.
