+++
date = '2024-11-04T22:39:48Z'
draft = false
tags = ['Python', 'Flask']
title = 'Flask environment configuration'
+++

init.py

```python
def create_app(config_setting):
	app = Flask(__name__)
	app.config.from_object(config[config_setting])
	admin = Admin(app, template_mode='bootstrap3')

	convention = {
		"ix": "ix_%(column_0_label)s",
		"uq": "uq_%(table_name)s_%(column_0_name)s",
		"ck": "ck_%(table_name)s_%(constraint_name)s",
		"fk": "fk_%(table_name)s_%(column_0_name)s_%(referred_table_name)s",
		"pk": "pk_%(table_name)s",
	}
	metadata = MetaData(naming_convention=convention)
	db = SQLAlchemy(app, metadata=metadata)

create_app(os.getenv('PRODCONFIG' or 'default')
```

config.py

```python
config = {
	'development': DevelopmentConfig,
	'production': ProductionConfig,
	'testing': TestingConfig,
	'default': DefaultConfig
}
```
