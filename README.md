```mermaid
erDiagram

 
  
  OCORRENCIA     }o--|| SENSOR         : detectada_por
  SENSOR         ||--o{ DADO_SENSOR    : gera
  
  
  RECURSO        ||--o{ DISPONIBILIDADE: possui

  

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
 USUARIO {
    int     id_usuario       PK
    string  nome
    string  cpf
    string  tipo_usuario
    string  localizacao
  }

  RECURSO {
    int     id_recurso       PK
    string  nome
    string  tipo
    string  localizacao
    int     usuario_id       FK
  }
USUARIO        ||--o{ OCORRENCIA     : relata
  USUARIO        ||--o{ RECURSO        : acessa
  DISPONIBILIDADE {
    int       id_disponibilidade  PK
    int       recurso_id          FK
    bool      status
    datetime  ultima_atualizacao
  }

 
```
