```mermaid
erDiagram

  USUARIO        ||--o{ OCORRENCIA     : relata
  USUARIO        ||--o{ RECURSO        : acessa
  USUARIO        ||--o{ INTERACAO      : gera
  OCORRENCIA     }o--|| SENSOR         : detectada_por
  SENSOR         ||--o{ DADO_SENSOR    : gera
  DADO_SENSOR    }o--|| SENSOR         : origem
  DADO_SENSOR    }o--|| RECURSO        : alimenta
  RECURSO        ||--o{ DISPONIBILIDADE: possui

  USUARIO {
    int     id_usuario       PK
    string  nome
    string  cpf
    string  tipo_usuario
    string  localizacao
  }

  OCORRENCIA {
    int       id_ocorrencia    PK
    string    tipo
    string    status
    datetime  data_hora
    string    localizacao
    int       usuario_id        FK
  }

  SENSOR {
    int     id_sensor        PK
    string  tipo_sensor
    string  localizacao
    string  dispositivo
  }

  DADO_SENSOR {
    int       id_dado          PK
    datetime  data_captura
    float     valor
    int       sensor_id        FK
    int       recurso_id       FK
  }

  RECURSO {
    int     id_recurso       PK
    string  nome
    string  tipo
    string  localizacao
    int     usuario_id       FK
  }

  DISPONIBILIDADE {
    int       id_disponibilidade  PK
    int       recurso_id          FK
    bool      status
    datetime  ultima_atualizacao
  }

  INTERACAO {
    int       id_interacao    PK
    int       usuario_id      FK
    datetime  data_hora
    string    tipo_acao
  }
```
