# Core Stack Modules

Additionally modules are built on these core interfaces, to provide more complex functionality such as user authentication or login.

## EventLogger

Provides a backend for semi-optimized storage of logging information. This is designed to be integrated with other tools (such as servlet, and accountTable) for additional meta-data, used in the logging process.

## Microservices, distributed / local lambda

Handles cron jobs, shared or exclusive jobs, etc.