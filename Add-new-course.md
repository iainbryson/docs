

* Add domain to nameserver `/var/named/chroot/etc/zone/compute.dtu.dk.head`
* Add CN dump user to CN course group
* Register CN dumper user at https://www.campusnet.dtu.dk/data/
* Get course element number at https://www.campusnet.dtu.dk/data/
* Add course in `/vol/config/courses.yaml`
* Add course in `/vol/config/couchdb.yaml` with random password
* Add course in `/vol/config/cn-dumper.yaml`
* Create Sharelatex admin user for the professor and send link
```
docker exec sharelatex /bin/bash -c "cd /var/www/sharelatex; grunt user:create-admin --email joe@dtu.dk"
```
* Ask professor to create ShareLatex project and share it read-only with `dtu@pdf.dumper`.
* Login as `dtu@pdf.dumper`and accept the shared project and get project number.
* Add course in `/vol/config/sharelatex.yaml`with project number.
* `cd /vol/quiz-keys; ssh-keygen -N '' -t rsa -f 0xxxx`
* `cd /vol/website-keys; ssh-keygen -N '' -t rsa -f 0xxxx-files`
* Create Github private repos `0xxxx` and `0xxxx-files`.
  * Copy/paste public keys to Github->Repo->Settings->Deploy Keys->Add Deploy key. Read/write.
  * Add professor in Github->Repo->Settings->Collaborators
* Add course in `/vol/config/quiz.yaml`
* Add course in `/vol/config/website.yaml`
