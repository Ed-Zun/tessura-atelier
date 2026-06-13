Here’s the process — two sides to it: GitHub and GoDaddy.

On GitHub

	1.	In your repository, go to Settings → Pages
	2.	Under “Source”, select your branch (usually main) and set the folder to / (root)
	3.	In the root of your repo, create a file named exactly CNAME (no extension) containing just your domain on one line:

strategictourist.nl


	4.	GitHub will show a green checkmark once it detects the CNAME file

On GoDaddy

Go to your domain’s DNS settings and add these records:



|Type |Name|Value                 |TTL|
|-----|----|----------------------|---|
|A    |@   |185.199.108.153       |600|
|A    |@   |185.199.109.153       |600|
|A    |@   |185.199.110.153       |600|
|A    |@   |185.199.111.153       |600|
|CNAME|www |yourusername.github.io|600|

The four A records point your apex domain (strategictourist.nl) to GitHub’s servers. The CNAME handles www.strategictourist.nl.

Then back on GitHub

Under Settings → Pages, type your custom domain (strategictourist.nl) in the “Custom domain” field and check Enforce HTTPS. GitHub will provision a free SSL certificate automatically via Let’s Encrypt — this can take 15–30 minutes after DNS propagates.

One gotcha with GoDaddy

GoDaddy sometimes has a pre-existing A record pointing @ to their parked page. Delete that one before adding the GitHub ones, otherwise you’ll have a conflict.

DNS propagation typically takes 30 minutes to a few hours, though it can occasionally take up to 24h.
