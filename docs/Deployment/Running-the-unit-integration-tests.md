The unit integration tests uses the type console to bootstrap a database then run sets of commands to compile types; create/update objects and run assert scripts to check the state.

The app.config in the Tesseract.Test project points at a Test database so that tests can be run independently of interactive use of the system (which usually is done in the Demo database). Set up a Test database using the instructions in [Setting up a local DEV environment](/Deployment/Setting-up-a-local-DEV-environment).



![image.png](/.attachments/image-7bdffd5b-b139-4d1e-b204-b9c302a37e1e.png)

NB: Two tests are currently failing. See #216

#60 has not been implemented yet.