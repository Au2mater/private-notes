---
mål: Prøv at bygge en første mobilapp
deadline: 2024-06-30
active_again_from: 2024-05-17
next_deadline: 
important:
---
### Moduler
- [ ] Use the FastUI ModelForm component to auto generate a form from the model.
- Manual Add / remove recipe url to recipe Collection
- [ ] Auto extract text from recipe link 
- [ ] Auto extract ingredient list from recipe text
- [ ] Add multiple recipes ingredient lists to interactive grocery shopping list 
- [ ] Interactive (grocery) checklist from ingredient list
- [ ] Standardize and sum quantity in grocery list 
- [ ] Store data on a cloud db
- [ ] Deploy Access  FASTApi webapp from phone
- [x] Deploy a webapp and access from phone

### Project resources ( delete /archive on archive )
* Forked repo https://github.com/Au2mater/msdocs-python-fastapi-webapp-quickstart
* https://github.com/hey-api/openapi-ts

### Features
* Søg efter opskrifter på nettet (Valdemarsro mm.)
	* Vælg kilder
* Tilføj opskrifter til madplan
* Tilføj egne opskrifter 
* Generer indkøbsliste fra madplan
* Beregner gns pris på opskrift ud fra online priser

### LOG 2024-05-12
* oprettet MS Azure konto under sarahs kumail Zkh64@alumni.ku.dk
* Fulgte denne guide [Quickstart: Deploy a Python (Django or Flask) web app to Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/quickstart-python?tabs=flask%2Cwindows%2Cazure-portal%2Cazure-cli-deploy%2Cdeploy-instructions-azportal%2Cterminal-bash%2Cdeploy-instructions-zip-azcli) 
	* Works natively with git repos + Flask og Django Framewrok 
	* For FASTApi a startup command must be specified in the configuration > https://learn.microsoft.com/en-us/azure/developer/python/configure-python-web-app-on-app-service