# Ansible CI/CD

## Setup process:
1. Download python dependencies:
`virtualenv venv`
`source venv/bin/activate`
`pip install -r requirements.txt`
2. Change `compose.yaml` for Windows or Mac:
```diff
         USERNAME: $USERNAME
     environment:
       PASSWORD: $PASSWORD
+    ports:
+      - mode: host
+        host_ip: 0.0.0.0
+        target: 22
+        published: 2222
+        protocol: tcp
     hostname: *service
     networks:
       - ci-cd
     restart: always
     deploy:
-      replicas: 5
+      replicas: 1
     privileged: true
```
3. Run ansible playbook:
`ansible-playbook -v -i inventory.yaml site.yaml`
