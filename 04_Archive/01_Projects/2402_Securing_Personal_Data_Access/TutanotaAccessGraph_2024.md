
```mermaid
---
title : "Access to Tutanota"
---
flowchart TD
A[Start] --> B([Acesss to your tutanota password?])
B -- yes --> C([Have access to Dashlane 2FA?])
C -- yes --> S[Access Tutanota Account] 
B -- no --> D([Have your recovery key & 2FA?])
D -- yes --> S
D -- no --> X[Acess Denied]
C -- no --> E([Have a recovery key?])
E -- yes --> S
E -- no --> X
style S fill:green,color:#fff;
style X fill:red,color:#fff;
```

Dashlane has both my password, 2FA and recovery key.
Without my Tutanota password and recovery code printed out, I permenantly loose access to tutanota if I loose access to Dashlane.   

### Steps to increase access 
- Print Recovery code