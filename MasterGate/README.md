#Proyecto de seguridad para aplicaciones y usuarios con autenticacion 2FA y JWT 

#Analista - Marino Castillo. Dominio - MDevelop

#Structura del proyecto 

MasterGate
|
├──src/
│
├── cmd/                    # Punto de entrada de la aplicación
│   └── api/
│       └── main.go         # Inicialización y configuración
│
├── config/                 # Configuración de la aplicación
│   ├── config.go           # Carga y validación de configuración
│   └── env/                # Variables de entorno por ambiente
│
├── internal/               # Código privado de la aplicación
│   ├── domain/             # Entidades y reglas de negocio
│   │   ├── entity/         # Modelos de dominio
│   │   │   ├── user.go
│   │   │   └── token.go
│   │   ├── repository/     # Interfaces de repositorios
│   │   │   └── user_repository.go
│   │   └── service/        # Interfaces de servicios
│   │       ├── auth_service.go
│   │       └── user_service.go
│   │
│   ├── infrastructure/     # Implementaciones concretas
│   │   ├── persistence/    # Implementación de repositorios
│   │   │   ├── postgres/
│   │   │   │   └── user_repository.go
│   │   │   └── redis/
│   │   │       └── token_repository.go
│   │   └── security/       # Implementaciones de seguridad
│   │       ├── jwt/
│   │       │   └── jwt_manager.go
│   │       └── totp/
│   │           └── totp_provider.go
│   │
│   ├── application/        # Casos de uso de la aplicación
│   │   ├── service/        # Implementación de servicios
│   │   │   ├── auth_service.go
│   │   │   └── user_service.go
│   │   └── dto/           # Objetos de transferencia de datos
│   │       ├── request/
│   │       │   ├── register_request.go
│   │       │   └── login_request.go
│   │       └── response/
│   │           ├── token_response.go
│   │           └── user_response.go
│   │
│   └── interfaces/         # Adaptadores de interfaces
│       ├── api/            # API HTTP
│       │   ├── handler/    # Controladores
│       │   │   ├── auth_handler.go
│       │   │   └── user_handler.go
│       │   ├── middleware/ # Middlewares
│       │   │   ├── auth_middleware.go
│       │   │   └── logger_middleware.go
│       │   └── router/     # Configuración de rutas
│       │       └── router.go
│       └── validator/      # Validación de datos
│           └── validator.go
│
├── migrations/             # Migraciones de base de datos
│   ├── 001_create_users_table.up.sql
│   └── 001_create_users_table.down.sql
│
├── pkg/                    # Código público que puede ser utilizado por otras aplicaciones
│   ├── logger/             # Implementación de logs
│   │   └── logger.go
│   └── errors/             # Manejo personalizado de errores
│       └── errors.go
│
├── test/                   # Pruebas
│   ├── integration/        # Pruebas de integración
│   └── mock/               # Mocks para pruebas
│
├── docs/                   # Documentación
│   ├── api/                # Documentación de la API (Swagger)
│   └── diagrams/           # Diagramas de arquitectura
│
├── deployments/            # Archivos de despliegue
│   ├── docker/             # Configuración Docker
│   │   ├── Dockerfile
│   │   └── docker-compose.yml
│   └── kubernetes/         # Configuración Kubernetes (si aplica)
│
├── scripts/                # Scripts de utilidad
│   ├── setup.sh
│   └── seed-data.sh
│
├── go.mod                  # Definición de módulo y dependencias
├── go.sum                  # Checksum de dependencias
├── .env.example            # Ejemplo de archivo de variables de entorno
├── .gitignore              # Archivos a ignorar por git
├── Makefile                # Comandos para construir, probar y ejecutar la aplicación
└── README.md               # Documentación del proyecto