# Node.js Graceful Shutdown Example

This repository demonstrates a common issue in Node.js applications: the lack of graceful shutdown when encountering unhandled exceptions or termination signals (like SIGINT, sent when you press Ctrl+C).

## The Problem

The `bug.js` file contains a simple HTTP server.  However, it doesn't handle the scenario where the server needs to shut down gracefully.  If you encounter an unhandled exception or send a SIGINT signal, the server might not properly close its connections, leading to resource leaks and potential data loss.

## The Solution

The `bugSolution.js` file shows how to address this issue using the `process` module's events.  By listening for `SIGINT` and `uncaughtException` events, the server can be instructed to shut down gracefully, allowing it to close existing connections before terminating.