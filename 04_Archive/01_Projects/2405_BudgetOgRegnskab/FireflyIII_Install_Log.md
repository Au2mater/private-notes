### LOG 2024-05-05
Successfully followed the guides below
- [How to install Firefly III with data importer using Docker](https://docs.firefly-iii.org/how-to/data-importer/installation/docker/)
	- Ændre volumen mapping i `docker-compose.yml`
```yml
...C:\Users\Bruger\OneDrive\01_Projects\2405_BudgetOgRegnskab\FireflyIII\firefly_iii_upload:/var/www/html/storage/upload
...C:\Users\Bruger\OneDrive\01_Projects\2405_BudgetOgRegnskab\FireflyIII\firefly_iii_db:/var/lib/mysql
...C:\Users\Bruger\OneDrive\01_Projects\2405_BudgetOgRegnskab\FireflyIII\import:/import
```

- `docker compose -f docker-compose.yml up -d --pull=always`
- Registered a new user , saved into Bitwarden
- [how to set up your first accounts](https://docs.firefly-iii.org/tutorials/finances/first-steps/)
- Data Importer 
	- Created a Client ID in Firefly iii under options - profile - OAuth
		- Name: `Lån og Spar Bank - Ahmad`
		- Redirect URL: `http://localhost:81/callback`
		- Confidential `False`
	- Copied the client id `3` and pasted it in the `Authenticate with Firefly III` startpage
	- [GoCardless](https://bankaccountdata.gocardless.com/overview/) setup
		- Created a GoCardless Account
		- [Connected to my bank](https://bankaccountdata.gocardless.com/data/)
		- [Created a new secret](https://bankaccountdata.gocardless.com/user-secrets/) saved the details in Bitwarden
		- In the Firefly Importer selected GoCardless as source and supplied the secret ID and key I just created
	- https://docs.firefly-iii.org/explanation/data-importer/about/gocardless-salt-edge/
	- [Automate the import](https://docs.firefly-iii.org/how-to/data-importer/import/automated/)