graph LR
    actor Administrador
    actor Cliente

    subgraph "Tienda Virtual"
        %% Casos de uso del Admin
        UC1("Crear nuevo catálogo de categorías")
        UC2("Modificar descripción de una categoría")
        UC3("Eliminar categoría")
        UC4("Crear nuevo producto")
        UC5("Modificar descripción y categoría de un producto")
        UC6("Eliminar producto")

        %% Casos de uso del Cliente
        UC7("Registrar ingreso inicial como cliente")
        UC8("Validar ingreso a la tienda virtual")
        UC9("Agregar producto al carrito de compra")
        UC10("Ver contenido del carrito de compra")
        UC11("Quitar producto del carrito de compra")
        UC12("Modificar cantidad de productos seleccionados")
        UC13("Finiquitar una compra")
        UC14("Mantener compra pendiente")

        %% Casos de uso compartidos
        UC15("Consultar catálogo de categoría")
        UC16("Consultar lista de productos por categoría")
        UC17("Ver detalles de un producto")
    end

    %% Conexiones del Administrador
    Administrador --> UC1
    Administrador --> UC2
    Administrador --> UC3
    Administrador --> UC4
    Administrador --> UC5
    Administrador --> UC6
    Administrador --> UC15
    Administrador --> UC16
    Administrador --> UC17

    %% Conexiones del Cliente
    Cliente --> UC7
    Cliente --> UC8
    Cliente --> UC9
    Cliente --> UC10
    Cliente --> UC11
    Cliente --> UC12
    Cliente --> UC13
    Cliente --> UC14
    Cliente --> UC15
    Cliente --> UC16
    Cliente --> UC17

    %% Relaciones Include y Extend
    UC13 --. "<<include>>" .-> UC8
    UC14 --. "<<include>>" .-> UC8
    UC10 --. "<<include>>" .-> UC8
    UC7 --. "<<extend>>" .-> UC8
    UC17 --. "<<extend>>" .-> UC16
