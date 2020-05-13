email in golang
=====
forked from https://github.com/jordan-wright/email
fix it so 163 email can use it (use ssl)

### Installation
```go get -u github.com/unievolver/email```

### Examples

#### SendWithTLS 
```go
	e := email.NewEmail()
	e.From = "name<lab@163.com>"
	e.To = []string{"lab@qq.com"}
	e.Subject = "subject"
	auth := smtp.PlainAuth("", "lab@163.com", "password", "smtp.163.com")
	e.HTML = []byte("<h1>HTML content </h1>")
	err := e.SendWithTLS("smtp.163.com:465", auth, nil)
	if err != nil {
		log.Println("Send Mail to", strings.Join(e.To, ","), " error:", err)
	}
	log.Println("Send Mail to", strings.Join(e.To, ","), " Successfully")
``` 

#### Another Method for Creating an Email
You can also create an email directly by creating a struct as follows:
```go
e := &email.Email {
	To: []string{"test@example.com"},
	From: "Jordan Wright <test@gmail.com>",
	Subject: "Awesome Subject",
	Text: []byte("Text Body is, of course, supported!"),
	HTML: []byte("<h1>Fancy HTML is supported, too!</h1>"),
	Headers: textproto.MIMEHeader{},
}
```

### Documentation
[http://godoc.org/github.com/unievolver/email](http://godoc.org/github.com/unievolver/email)
