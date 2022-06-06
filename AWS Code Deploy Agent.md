# AWS Code Deploy Agent

### Issue with agent not being able to start

Error says nothing - the service is unable to start. After a lot of fiddling removing it with sudo apt-get purge codedeploy-agent and reinstalling it manually using amazon instructions helped (keep in mind that ubuntu 20.04. requires a workaround in install).

### Issue with deploy containing many core.\*\*\*\*\*\*\* archives that bloat deploy size

The issue is, that during testing on build stage, somehow it creates these archives in projects root directory. Simplest solution is to add ```rm -rf code*``` after tests run.