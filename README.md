```mermaid
erDiagram
    MEMBRESIAS {
        ObjectId _id
        string descripcion
        number duracion_dias
        number precio
        string estado
    }

    SOCIOS {
        ObjectId _id
        string dni
        string nombre
        string apellido
        string telefono
        string mail
        date fecha_inicio
        date fecha_pago_cuota
        date fecha_baja
        string estado
        ObjectId id_membresia
    }

    USUARIOS {
        ObjectId _id
        string dni
        string nombre
        string apellido
        string telefono
        string mail
        string password
        string cargo
        string rol
        date fecha_alta
        date fecha_baja
        string estado
    }

    PAGOS {
        ObjectId _id
        ObjectId id_socio
        ObjectId id_membresia
        number monto
        date fecha_pago
        ObjectId registrado_por
        string observaciones
    }

    MEMBRESIAS ||--o{ SOCIOS : "asignada a"
    MEMBRESIAS ||--o{ PAGOS : "incluida en"
    SOCIOS ||--o{ PAGOS : "tiene"
    USUARIOS ||--o{ PAGOS : "registra"