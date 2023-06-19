## Simple Book-Info app
This is a simple book-info app which requires mysql db to store information about books and expose two api endpoints to add and view books

## Installing app on kubernetes
```
kubectl apply -f app/database.yaml
kubectl apply -f app/app.yaml
```

## Access API endpoints to add and view books

First port forward the book-info app service to access the endpoints

```
kubectl port-forward svc/book-info 80:80
```

1. Add Book
   ```
   curl -XPOST http://localhost/addbook -d '{"isbn": 9781982156909, "title": "The Comedy of Errors", "synopsis": "The authoritative edition of The Comedy of Errors from The Folger Shakespeare Library, the trusted and widely used Shakespeare series for students and general readers", "authorname": "William Shakespeare", "price": 10.39}'
   ```
2. View Books
   ```
   curl -XGET http://localhost/getbooks
   ```