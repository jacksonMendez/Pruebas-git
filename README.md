# 🏥 SmartHealth RAG – Backend del Proyecto Final

**SmartHealth RAG** es un sistema backend que permite realizar consultas clínicas inteligentes utilizando el patrón **RAG (Retrieval-Augmented Generation)**.  
El proyecto combina datos reales almacenados en PostgreSQL con búsquedas vectoriales mediante **pgvector**, integrando un modelo de lenguaje (LLM) para generar respuestas basadas estrictamente en la información disponible en la base de datos.

Incluye autenticación con JWT, auditoría completa, un endpoint principal para consultas y soporte WebSocket para respuestas en tiempo real. Además, este backend está preparado para conectarse a un **frontend básico tipo chat**, desarrollado como parte del mismo proyecto.

---

## 🧠 Descripción General

El sistema permite que un usuario autenticado consulte información clínica de un paciente enviando su tipo y número de documento junto con una pregunta.  
El backend se encarga de:

- Obtener datos clínicos desde PostgreSQL.  
- Ejecutar búsquedas semánticas con embeddings y pgvector.  
- Construir el contexto que alimenta al LLM.  
- Generar una respuesta en formato JSON estricto.  
- Registrar cada consulta en auditoría.

El objetivo es garantizar respuestas correctas, rastreables y basadas exclusivamente en datos existentes.

---

## 🏛 Arquitectura del Sistema

El proyecto está construido con:

- **FastAPI** como framework principal.  
- **PostgreSQL** + **pgvector** para almacenamiento y búsqueda vectorial.  
- **JWT** para autenticación.  
- **WebSocket** para comunicación token-by-token.  
- **LLM** local o por API para la generación final.

### Flujo simplificado:
1. Usuario inicia sesión.  
2. Envía una consulta clínica.  
3. El backend recupera datos + ejecuta similarity search.  
4. Se genera la respuesta con el LLM usando únicamente datos válidos.  
5. Se registra la auditoría y se responde al cliente.  

---

## 🗂 Datos y Auditoría

- **users:** Manejo de cuentas del sistema.  
- **audit_logs:** Registro de cada consulta, incluyendo sesión, pregunta y respuesta generada.  

Este diseño asegura trazabilidad y control de todo el funcionamiento del sistema.

---

## 🔌 Endpoints Principales

- **POST /auth/register** – Registro de usuarios.  
- **POST /auth/login** – Autenticación con JWT.  
- **POST /query** – Ejecución completa del flujo RAG y retorno de respuesta JSON.  
- **WS /ws/chat** – Respuestas en tiempo real vía WebSocket.

---

## 🎨 Integración con el Frontend

El backend está preparado para conectarse con un **frontend tipo chat**, que forma parte del proyecto.  
Este frontend permitirá:

- Iniciar sesión  
- Enviar consultas  
- Ver respuestas en formato chat  
- Conectarse al WebSocket para recibir mensajes en tiempo real  

---

## 🧩 Componentes Principales

- Autenticación segura (JWT)  
- Motor RAG (consulta SQL + vector search + LLM)  
- Auditoría completa  
- Streaming en vivo  
- BD clínica estructurada  

---

## 📎 Recursos y Documentación

El proyecto utiliza documentación oficial sobre RAG, embeddings, PostgreSQL, pgvector y arquitectura de APIs modernas.

---

## 👥 Equipo

Proyecto desarrollado para SmartHealth – 2025-2.  


