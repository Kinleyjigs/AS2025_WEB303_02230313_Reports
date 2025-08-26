
# WEB303 – Microservices & Serverless Applications  
## Practical 2: API Gateway with Service Discovery  

### Overview  
In this practical, I built a small microservices ecosystem with:  
- **Users Service** (manages user data)  
- **Products Service** (manages product data)  
- **API Gateway** (acts as the single entry point)  
- **Consul** (used as the service registry and health checker)  

The API Gateway dynamically discovers healthy services through Consul and routes requests accordingly. This setup allows services to be restarted, scaled, or updated without reconfiguring other parts of the system.  

---

### Learning Outcomes Achieved  
- **LO2**: Designed and implemented microservices in Go using REST and service discovery.  
- **LO8**: Implemented observability features such as health checks and logging with Consul.  


- **API Gateway** → Receives all external requests, consults Consul, forwards to the right service.  
- **Consul** → Keeps a “phone book” of healthy services.  
- **Users-Service** → Registers itself with Consul, exposes `/users/{id}` endpoint.  
- **Products-Service** → Registers itself with Consul, exposes `/products/{id}` endpoint.  

---

### 🛠 Steps Taken  

1. **Set up Consul**  
   - Ran Consul in development mode (`consul agent -dev -ui`).  
   - Verified Consul UI at `http://localhost:8500`.  

2. **Implemented Users-Service**  
   - Built in Go with `chi` router.  
   - Registers with Consul on startup.  
   - Exposes `/users/{id}` endpoint.  

3. **Implemented Products-Service**  
   - Similar to Users-Service but on port `8082`.  
   - Exposes `/products/{id}` endpoint.  

4. **Implemented API Gateway**  
   - Routes requests from `/api/users/*` → Users-Service.  
   - Routes requests from `/api/products/*` → Products-Service.  
   - Uses Consul API client for service discovery.  

5. **Tested the System**  
   - Verified both services registered as **healthy** in Consul.  
   - Sent requests via API Gateway using cURL/Postman.  
   - Confirmed correct responses and routing.  

6. **Resilience Demonstration (Bonus)**  
   - Stopped Users-Service → Gateway reported “no healthy instances”.  
   - Restarted service → Gateway automatically routed requests again.  

---

### 📸 Screenshots  

- **Consul UI showing both services registered and healthy**

![alt text](<practical2_images/Screenshot 2025-08-22 at 1.59.38 AM.png>)

- **Requests via terminal/cURL**  

![alt text](<practical2_images/Screenshot 2025-08-22 at 1.16.15 PM.png>)

- **API Gateway terminal logs**  

![alt text](<practical2_images/Screenshot 2025-08-22 at 1.19.32 PM.png>)

---

### Repository Link

https://github.com/Kinleyjigs/AS2025_WEB303_02230313_Practical2.git