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
  
  -----------------------------------------------------------------------------------------
  
  Discovering Services from Other Projects
To Discover a service located in a different project than the 3scale project, 3scale needs view permissions into the project where that service exists. To give 3scale access to other projects, the 3scale amp service account must have the view role.

$ oc policy add-role-to-user \
  view system:serviceaccount:3SCALE_PROJECT:amp -n PROJECT_NAME
You can also give 3scale access to all the projects in the cluster by assigning it the view role as a cluster role.

$ oc adm policy add-cluster-role-to-user view \
  system:serviceaccount:3SCALE_PROJECT:amp
