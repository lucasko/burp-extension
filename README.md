
### Add X-forwarded-For with Random IP into Request

```
	if messageIsRequest :
		messageInfo = message.getMessageInfo()
		headers =  self.helpers.analyzeRequest(messageInfo.getRequest()).getHeaders() 
		for header in  headers :

			ip = ".".join(map(str, (random.randint(0, 255)  for n in range(4))))
			xforward = "X-Forwarded-For: " + ip
			headers.add(xforward)
			newRequest = self.helpers.buildHttpMessage(headers ,  None) 
			messageInfo.setRequest(newRequest)
```
