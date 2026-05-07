# Roman

Personal multi-agent harness. The diagram's the flow/artifact.

![Architecture](roman.svg)

This is the wrapping I run around Claude on a Mac mini. The model is the cheap part. The system around it is what makes it run unsupervised across long-running work: file locks on shared state, runtime hooks gating worker writes before bad output ships, an evaluator that rejects ambiguous specs before they get dispatched, an append-only completion log, and dedupe on outbound notifications so retries don't spam. Thirteen workers, each with a defined scope and a permission boundary. None of them are clever in isolation.
