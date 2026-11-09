---
'evlog': minor
---

Add `log.discard()` to drop a wide event that has nothing to report, such as an idle cron run. The event is not written, enriched or drained, even when an integration emits it for you, and neither `keep` nor head sampling can keep it. An event that records an error, a fatal message or an audit still emits, so a unit that fails after `discard()` is never dropped. In `evlog/effect`, `withLogger(action, { emit: 'onError' })` emits a job's event only when the job fails or records an error or an audit: a success or an interruption emits nothing.
