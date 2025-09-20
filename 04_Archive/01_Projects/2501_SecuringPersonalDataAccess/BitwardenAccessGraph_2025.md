
```mermaid
---
title : "Access to Bitwarden"
---
flowchart TD
A[Start] --> B(["`Recall **Account Email adress**?`"])
B -- yes --> C([Have access to 2FA app/email?])
C -- yes --> D([Recall Password?])
D -- yes --> S[Access Granted] 
B -- no --> X[Acess Denied]
C -- no --> E([Have access to SSD with 2FA recovery key?])
E -- yes --> D
E -- no --> X
D -- no --> F(["`Emergency Contact?`"])
F -- yes --> S
F -- no --> X
style S fill:green,color:#fff;
style X fill:red,color:#fff;
```

### References
[I Forgot my Master Password \| Bitwarden](https://bitwarden.com/help/forgot-master-password/)
* Opsætning af totrins-login kan permanent låse en bruger ude af sin Bitwarden-konto. En gendannelseskode muliggør kontoadgang, såfremt den normale totrins-loginudbyder ikke længere kan bruges
* 2FA Både email og Authy