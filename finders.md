# Finders
Finders are pretty much the same as models in the MVC architecture. They help you retrieve records from the database.

Simple usage example (in a controller):
```
$finder = $this->finder('XF:User');
$users = $finder->where('user_id', 20)->fetchOne();
```