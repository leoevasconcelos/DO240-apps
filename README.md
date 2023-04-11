# DO240-apps

Install API Books

oc new-app \
  --name=books-api \
  --context-dir=library/books-api \
  --build-env NODE_ENV=development \
  https://github.com/leoevasconcelos/DO240-apps.git
  
  
  -----------------------------------------------------------------------------------------
  Add Service 3scale discovery
  
  oc label svc/books-api \
  discovery.3scale.net="true"
