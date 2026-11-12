## 💖 Сборка и запуск проекта

#### Старт

```bash
cd backend
poetry config virtualenvs.in-project true
poetry install
poetry env activate # выводит команду активации виртуального окружения
# выполняем команду активации виртуального окружения
```

#### Запуск

1. Без докера
```bash
cd backend
uvicorn app.main:app --reload
```

2. С докером
```bash
docker-compose up --build

docker-compose up backend frontend postgres # определенные сервисы

docker-compose down

docker-compose logs -f backend # просмотр логов
```

## 📀 Структура проекта

```angular2html
basketball-fact-ranking/
├── backend/                            # FastAPI сервис
│   ├── app/                            # API и бизнес логика
│   │
│   ├── config.py                       # Загрузка и проверка конфигурации из .env
│   ├── pyproject.toml                  # Зависимости для backend
│   ├── poetry.lock                     # Зависимости в моменте?
│   └── Dockerfile                      # Dockerfile для backend
│
├── docs/                               # Документация
│   ├── rules.md                        # Правила добавления кода / git команды
│   └── setup.md                        # Информация о проекте / сборке и запуске
│
├── docker-compose.yml                  # Сборка всех контейнеров
├── .env                                # Значения конфигурации
├── .gitignore                          # Ненужные для git файлы
└── README.md                           # Основное описание проекта
```

### Непонятные папки и файлы:

1. `base.py` 

    - Содержание 
    ```python
    from sqlalchemy.orm import DeclarativeBase
    
    class Base(DeclarativeBase):
        pass
    ```

    - Использование
        ```python
        from db.base import Base
        ```
    
        `Base` нужен для того, чтобы:
        * все модели наследовались от одного класса;
        * SQLAlchemy собрал информацию обо всех таблицах (`Base.metadata`);
        * можно было выполнить:
        ```python 
        Base.metadata.create_all(engine)
        ```

2. `config.py` 

    - Содержание 
    ```python
    from pydantic_settings import BaseSettings, SettingsConfigDict
    
    
    class Settings(BaseSettings):
        database_url: str
        khl_base_url: str
        goalserve_url: str
    
        headless: bool = True
        log_level: str = "INFO"
    
        model_config = SettingsConfigDict(
            env_file=".env",
            extra="ignore",
        )
    
    
    settings = Settings()
    ```

    - Использование (после создания файла в любом месте проекта можно написать)

        ```python
        from config import settings
        
        engine = create_engine(settings.database_url)
        ```
        ИЛИ
        ```python
        response = requests.get(settings.khl_base_url)
        ```