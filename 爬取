import requests
import re
def get():
	try:	
		information=open("information.txt","rt")
	except:
		return 0;	
	login=information.readline()
	login=login.split("\n")[0]
	password=information.readline()
	password=password.split("\n")[0]
	repositories=information.readline()
	repositories=repositories.split("\n")[0]
	filename=input("要爬取的文件")

	
	
	url1="https://github.com/session"
	url2="https://github.com/"+str(login)+"/"+str(repositories)
	url3=url2+"/blob/master/"+filename
	
	data_denglu={
        "commit":"Sign+in",
        "utf8":"✓",
        "authenticity_token":"BQ775aXgK0ZlS6BKPrMuIOiVbDezQj7DQpzpA6MzwmQIxPL4wk1VvO8tXAJuCFMNk/zvI4ysMvVOxOPWZ+Jnmg==",
        "login":login,
        "password":password}
	cookies_denglu={
        "_ga":"GA1.2.753903281.1505531409",
        "_gh_sess":"eyJzZXNzaW9uX2lkIjoiZjY4MTBiZDY4YzkwYTA0YWQ0YTM3MmJlNjdlZjU0ZDEiLCJsYXN0X3JlYWRfZnJvbV9yZXBsaWNhcyI6MTUwOTAwMjQ2NTY1MSwiY29udGV4dCI6Ii8iLCJzcHlfcmVwbyI6InpodXpodXhpYWVpLy0iLCJzcHlfcmVwb19hdCI6MTUwOTAwMjMyNSwibGFzdF93cml0ZSI6MTUwOTAwMjM0NjYxOSwicmVmZXJyYWxfY29kZSI6Imh0dHBzOi8vZ2l0aHViLmNvbS8iLCJfY3NyZl90b2tlbiI6ImNiL0FoaEN2cmlVVXVSNURSendlcHFZUlNqL0prNXNwdS9JUSs4RXlESzQ9IiwiZmxhc2giOnsiZGlzY2FyZCI6W10sImZsYXNoZXMiOnsiYW5hbHl0aWNzX2xvY2F0aW9uX3F1ZXJ5X3N0cmlwIjoidHJ1ZSJ9fX0=--5ae52916dd2bdd5ea254116d0cc8793b05366b3b",
        "_octo":"GH1.1.368302907.1505531424",
        "logged_in":"no",
        "tz":"Asia/Shanghai"
        }
    
   
	s=requests.Session()
	
	r1=s.post(url=url1,data=data_denglu,cookies=cookies_denglu)
	
	r2=s.get(url=url2)
	
	
	params={"_pjax":"#js-repo-pjax-container"}
	r3=s.get(url=url3,params=params)
	print(r3.status_code)
	TEXT=re.findall(r'js-file-line\">.*?</td>',r3.text)
	try:
		localfile=open(filename,'wt')
	except:
		print("创建本地文件失败")
		return 0;
	for line in TEXT:
		line=line[14:-5]
		print(line,file=localfile)		
	
		
	return 0;
get()
