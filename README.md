# **Custom ELT Pipeline with Docker & PostgreSQL**  

This repository showcases a **custom Extract, Load, Transform (ELT) pipeline** using **Docker** and **PostgreSQL**. It demonstrates a complete ELT process by transferring data from a source database to a destination database within a containerized environment.  

## **📂 Repository Structure**  

### 🔹 **Configuration & Orchestration**  
- **`docker-compose.yaml`** – Defines three services:  
  - `source_postgres` → Source PostgreSQL database with sample data.  
  - `destination_postgres` → Target PostgreSQL database.  
  - `elt_script` → Runs the ELT process.  

### 🔹 **ELT Process**  
- **`elt_script/Dockerfile`** – Sets up a **Python environment** with the necessary dependencies.  
- **`elt_script/elt_script.py`** – The **core ELT script**:  
  - Waits for the source database to be ready.  
  - Uses `pg_dump` to extract data.  
  - Loads the extracted data into the destination database using `psql`.  

### 🔹 **Database Initialization**  
- **`source_db_init/init.sql`** – Initializes the **source database** with sample data, creating tables such as:  
  - Users  
  - Films  
  - Film categories  
  - Actors  
  - Film actors  

## **⚙️ How It Works**  

1️⃣ **Containerized Environment** – Docker Compose orchestrates three containers (source DB, destination DB, ELT script).  
2️⃣ **Database Initialization** – The `init.sql` script sets up the source database with predefined sample data.  
3️⃣ **ELT Execution** – The Python script:  
   - Waits for the source database.  
   - Dumps data using `pg_dump`.  
   - Loads it into the destination database using `psql`.  
4️⃣ **Post-Execution Access** – Both databases can be accessed via ports **5433** (source) and **5434** (destination).  

## **🚀 Getting Started**  

1️⃣ **Prerequisites**: Ensure you have **Docker** and **Docker Compose** installed.  
2️⃣ **Clone the Repository**:  
   ```bash
   git clone https://github.com/your-username/custom-elt-project.git
   cd custom-elt-project
   ```  
3️⃣ **Start the Containers**:  
   ```bash
   docker-compose up
   ```  
4️⃣ **Monitor Execution**: Once running, the ELT process will transfer data automatically.  
5️⃣ **Verify Databases**: Connect to PostgreSQL instances:  
   ```bash
   psql -h localhost -p 5433 -U user -d source_db  # Source DB  
   psql -h localhost -p 5434 -U user -d destination_db  # Destination DB  
   
