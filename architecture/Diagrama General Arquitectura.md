---
config:
  theme: default
  layout: dagre
---
flowchart LR
 subgraph subGraph0["Nucleo de la Solucion"]
        Micro["Microservicio Reservas"]
        API["API Gateway"]
        DB[("Cloud SQL")]
  end
 subgraph subGraph1["Ecosistema Google"]
        GCal["Google Calendar"]
        GAuth["Google Identity"]
  end
    User["Usuario"] --> Web["Interfaz Web"]
    Web --> API
    API --> Micro & GAuth
    Micro --> DB & GCal
