Requirements
------------

Target platform should be an ubuntu with apt-get capabilities

Role Variables
--------------

# Repositories to clone 

The project name will be used to test the api url from redmine and the apikey that will be used for githook
Do not use ssh repos, it will not work due that we are not managing ssh keys.

    redmine_repositories:
      reponame:
        project: "project_name_to_associate"
        repositoryurl: "https://somehost/someuser/repo.git"
        repositorydir: "name.git"

For private repos use user:pass@somehost

# User to clone git-repositories

    redmine_git_repos: "/opt/repositories"
    redmine_git_user: "www-data"
    redmine_git_user_password: "generate it with normal mkpasswd"

# Test gitlab_hook plugin
### After installing redmine go to admin / settings / repositories

Ensure you have configured Redmine/settings/gitlab_hook plugin enabled for all branches as it uses --mirror



    # Enable: Enable WS for repository management
    # Paste here your key
    redmine_api_key: "somecode"

Ensure you have added your group_vars/redmine_servers/redmine_repos redmine_api_key value, before running this role.

And add `redmine_git_test_gitlabhook: true` to your vars


Adding repositories
==================

To clone a repositories you must edit redmine_repositories var as shown in Vars. 

If you have gitlab_hooks plugin:

Add to the web hooks:

http://redmineuy.group.upm.com/gitlab_hook?project_id=yourassociatedprojectforthisrepo&key=yourredmine_api_key

(don't use ssl verification for this case)

Add the repository to your project in redmine /projects/projectname/settings/repositories

on location path, just use the path specified in `redmine_git_repos`/`repositorydir` per repository synchronized


License
-------

MIT

Author Information
------------------
Pablo Estigarribia

pablodav at gmail
