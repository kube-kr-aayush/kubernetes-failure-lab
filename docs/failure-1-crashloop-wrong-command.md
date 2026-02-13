# Failure 1 – CrashLoopBackOff (Wrong Command)

## What Broke
Pod entered CrashLoopBackOff state immediately after deployment.

## Symptoms
- Pod status: CrashLoopBackOff
- Restart count increasing

## Debugging Steps
- kubectl get pods
- kubectl describe pod crashloop-wrong-command
- kubectl logs crashloop-wrong-command

## Root Cause
The container was configured with an invalid command:
command: ["wrong-command"]

The nginx image does not contain this executable, causing immediate container failure.

## Fix
Remove incorrect command or use valid nginx start command.

## Key Learning
If a container exits immediately, check:
- command
- entrypoint
- logs
- exit code

