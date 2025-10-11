# api-service

Options (template variables):
- Router: chi | gorilla | httprouter | servemux (default: servemux)
- DB: sqlite-native | sqlite-gorm | postgres-native | postgres-gorm | mysql-native | mysql-gorm (default: sqlite-native)

Examples:
dragon gen -b api-service -o mysvc
dragon gen -b api-service -o mysvc --router chi --db postgres-gorm
