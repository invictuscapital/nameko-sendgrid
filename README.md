# nameko-sendgrid
SendGrid dependency for nameko services

## Installation
```python
pip install nameko-sendgrid
```

## Usage
```python
from nameko.rpc import rpc
from nameko_sendgrid import SendGrid
from sendgrid.helpers.mail import *


class Service:
    name = "service"
    
    sendgrid = SendGrid()
    
    @rpc
    def send_email(self, address, body):
        from_email = Email("test@example.com")
        to_email = Email(address)
        subject = "Sending with SendGrid is Fun"
        content = Content("text/plain", body)
        message = Mail(from_email, subject, to_email, content)
        
        self.sendgrid.client.mail.send.post(message)
```

Specify your configuration like this:
```yaml
SENDGRID_KEY: abcd
```
