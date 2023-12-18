### OWASP juice shop demo

https://pwning.owasp-juice.shop/companion-guide/latest/introduction/README.html
https://github.com/juice-shop/juice-shop

## Intro
- owasp: open worldwide app application security project
	- Community-led open source software projects
	- Over 250+ local chapters worldwide
	- Tens of thousands of members
	- Industry-leading educational and training conferences
- top 10
	- injection
	- xss
	- broken authentication
	- broken access control
	- insecure design / security misconfiguration
	- insecure logging
- owasp juice shop
- Burp usage
### Install:
- (install docker)
- docker pull bkimminich/juice-shop
- docker run --rm -p 3000:3000 bkimminich/juice-shop

[Injection](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A1-Injection)
- types: sql, command and email
- it's time to talk about SQL injections:
	- how should a query look like for an authentication
	- **select user u from users where u.name = 'form.name' and u.password = 'form.password'**
- how does injection come into the picture? 
- use 'or 1=1-- in user or '--
	- select user u from users where u.name = 'form.name=='--== ' and u.password = 'form.password'
	- select user u from users where u.name = 'form.name==' or 1=1 --== ' and u.password = 'form.password'

[Broken Authentication](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A2-Broken_Authentication)
- reset admin password - brute force with burp intruder
- real world breach: 
	- instagram account takeover
	- 6 digit code to change passw
	- 200 guess / IP  (no limit for guesses for multiple IP requests)
	- researcher used 5000 IPs in a second

[Sensitive Data Exposure](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A3-Sensitive_Data_Exposure)
- /ftp path in /about
- exposing versions and logs

[Broken Access Control](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A5-Broken_Access_Control)
![image](https://github.com/radopeti/stuff/assets/13570657/3ace6b33-527c-4408-a0c0-36fa23ae4c1d)

- real world breach:
	- **broken object level auth:** coinbase, params changed in the api call, sold crypto he did not owned
		![image](https://github.com/radopeti/stuff/assets/13570657/99adacea-a7fb-41c3-a2ff-7b209b9d42d6)


[Cross-Site Scripting XSS](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A7-Cross-Site_Scripting_(XSS))
- DOM 
	- `<IMG SRC="https://gremmedia.hu/storage/app/uploads/public/5ea/f3d/da3/5eaf3dda3e6f8918839096.png" onmouseover="alert('xxs')">`
	- `<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>`
- Persistent
- Reflected

## Other resources for practise:
- tryhackme.com / owasp top10 boxes
- https://www.secureflag.com/ / code specific challenges
- https://portal.securecodewarrior.com/#/login / code specific challenges
