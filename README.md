# Repro for issue 7774

## Versions

firebase-tools: v13.20.2<br>
python: v3.11.6

## Steps to reproduce

1. Create a venv
   - Run `cd functions`
   - Run `python3.11 -m venv venv`
   - Run `. venv/bin/activate`
2. Installing dependencies
   - Run `python3.11 -m pip install -r requirements.txt`
3. Run `cd ../`
4. Run `firebase deploy --only functions --project PROJECT_ID`
   - Outputs:

```
$ firebase deploy --only functions --project PROJECT_ID

=== Deploying to 'PROJECT_ID'...

i  deploying functions
i  functions: preparing codebase default for deployment
i  functions: ensuring required API cloudfunctions.googleapis.com is enabled...
i  functions: ensuring required API cloudbuild.googleapis.com is enabled...
i  artifactregistry: ensuring required API artifactregistry.googleapis.com is enabled...
✔  functions: required API cloudbuild.googleapis.com is enabled
✔  functions: required API cloudfunctions.googleapis.com is enabled
✔  artifactregistry: required API artifactregistry.googleapis.com is enabled
i  functions: Loading and analyzing source code for codebase default to determine what to deploy
 * Serving Flask app 'serving'
 * Debug mode: off

WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://127.0.0.1:8081

Press CTRL+C to quit

127.0.0.1 - - [02/Oct/2024 00:19:45] "GET /__/functions.yaml HTTP/1.1" 200 -

127.0.0.1 - - [02/Oct/2024 00:19:45] "GET /__/quitquitquit HTTP/1.1" 200 -

/bin/sh: line 1: 92796 Terminated: 15          python3.11 "/Users/<PATH>/issues/7774/functions/venv/lib/python3.11/site-packages/firebase_functions/private/serving.py"

i  functions: preparing functions directory for uploading...
i  functions: packaged /Users/<PATH>/issues/7774/functions (1.4 KB) for uploading
i  functions: ensuring required API run.googleapis.com is enabled...
i  functions: ensuring required API eventarc.googleapis.com is enabled...
i  functions: ensuring required API pubsub.googleapis.com is enabled...
i  functions: ensuring required API storage.googleapis.com is enabled...
✔  functions: required API eventarc.googleapis.com is enabled
✔  functions: required API pubsub.googleapis.com is enabled
✔  functions: required API storage.googleapis.com is enabled
✔  functions: required API run.googleapis.com is enabled
i  functions: generating the service identity for pubsub.googleapis.com...
i  functions: generating the service identity for eventarc.googleapis.com...
✔  functions: functions folder uploaded successfully
i  functions: creating Python 3.11 (2nd Gen) function on_request_example(us-central1)...
✔  functions[on_request_example(us-central1)] Successful create operation.
Function URL (on_request_example(us-central1)): <RUN_URL>
i  functions: cleaning up build files...

✔  Deploy complete!
```
