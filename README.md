# oracle_pdb_ass_II__29007_marnisse
# Oracle PDB Administration Assignment - INSY 8311

**Student:** Marnise  
**ID Number:** 29007  
**Course:** Database Development with PL/SQL (INSY 8311)  
**Instructor:** Eric Maniraguha  
**Date:** 16th February 2026










## Assignment Tasks

### Task 1: Permanent Pluggable Database Creation

**Goal:** Establish a new PDB with appropriate user credentials following specified naming standards.

**Implementation Steps:**
1. Established connection to the container database with SYSDBA privileges
2. Generated pluggable database: `ma_pdb_29007`
3. Activated the PDB in READ WRITE operational mode
4. Navigated into the PDB container context
5. Established user account: `marnise_plsqlauca_29007`
6. Assigned necessary privileges (CONNECT, RESOURCE, DBA)
7. Validated successful user account creation

**SQL Implementation:**










**Documentation:**
-  Temporary PDB creation
- <img width="544" height="140" alt="task 1 user created verification" src="https://github.com/user-attachments/assets/81206b02-a297-441d-9946-dc7ad293d353" />

- Evidence: PDB existence confirmation
- Evidence: Successful PDB removal execution
- <img width="514" height="130" alt="Task 2 deletion of temp pdb" src="https://github.com/user-attachments/assets/1cb707d1-97e5-491e-9331-77d5408f0a92" />

- Evidence: Removal verification (no rows returned)
- <img width="514" height="130" alt="Task 2 deletion of temp pdb" src="https://github.com/user-attachments/assets/61bace5d-80f8-468c-b2b8-ae14011c95f3" />


- Creation of the user
- <img width="433" height="46" alt="task1 creating user" src="https://github.com/user-attachments/assets/d91c6b64-c0e9-4af9-bdc3-46d35f2279b0" />
Creation of PDB
<img width="518" height="157" alt="task1 pdb creation" src="https://github.com/user-attachments/assets/eb46a804-d051-460b-aa7b-7f28b2d1fbec" />






### Task 3: Database Monitoring with Oracle Enterprise Manager

**Goal:** Access and document the database environment using Oracle's web-based management interface.

**Implementation Steps:**
1. Navigated to OEM interface (https://localhost:5500/em)
2. Authenticated using SYSTEM credentials
3. Accessed Database Home dashboard
4. Reviewed container database configuration with active PDBs
5. Documented visual representation of database resources

**Dashboard Details:**
- Database Instance: XE (21.3.0.0.0)
- Instance Type: Single Instance (xe)
- Architecture: Container Database with multiple pluggable databases
- System Platform: Microsoft Windows x86 64-bit
- Visual Confirmation: MA_PDB_29007 visible in Data Storage visualization

**Documentation:**
- Evidence: Complete OEM dashboard screenshot with PDB visualization
- 
- <img width="1874" height="830" alt="pdb visualization" src="https://github.com/user-attachments/assets/fb103d08-0fd0-4456-944c-f13bcb3bcdc7" />


---

### Task 4: Professional Documentation & Repository

**Repository Organization:**


## Technical Challenges & Resolutions

### Challenge 1: Data File Path Configuration
**Issue:** Initial PDB creation failed due to incorrect data file destination path specification.

**Resolution Approach:** 
- Executed query against v$datafile system view to identify actual data file location
- Identified correct path: `C:\APP\MARNISSE\PRODUCT\21C\ORADATA\XE`
- Applied CREATE_FILE_DEST parameter with verified path
- Achieved successful PDB creation

### Challenge 2: Container Context Management
**Issue:** Ensuring operations execute within appropriate container context (CDB root vs specific PDB).

**Resolution Approach:**
- Implemented ALTER SESSION SET CONTAINER for context switching
- Confirmed container context prior to operation execution
- Recognized that user creation requires PDB container context

---

## Knowledge Acquired

1. **Multitenant Architecture:** Comprehensive understanding of CDB and PDB relationships
2. **PDB Management:** Proficiency in PDB creation, activation, and removal operations
3. **Context Awareness:** Critical importance of container context for different database operations
4. **User Administration:** Creating and configuring users within isolated PDB environments
5. **Problem Resolution:** Diagnosing and resolving path configuration and context issues
6. **Monitoring Tools:** Utilizing Oracle Enterprise Manager for database oversight
7. **Documentation Standards:** Maintaining precise naming conventions and comprehensive documentation

---

## Integrity Declaration

I, Marnise (Student ID: 29007), affirm that this submission represents my individual work. All database operations were performed personally, and all evidence screenshots originate from my Oracle Database installation. I have maintained academic integrity by not copying from peers and not utilizing artificial intelligence tools for solution generation. This assignment reflects my personal comprehension and hands-on execution of Oracle Pluggable Database administration.

---

## Deliverables Summary

### Database Objects Created:
- **Production PDB:** ma_pdb_29007 (operational in READ WRITE mode)
- **User Account:** marnise_plsqlauca_29007 (configured with CONNECT, RESOURCE, DBA privileges)
- **Temporary PDB:** ma_to_delete_pdb_29007 (created and subsequently removed)

### Evidence Provided:
Complete screenshot documentation demonstrating successful completion of all assignment requirements.

---

## Repository Details

- **Repository Identifier:** oracle_pdb_ass_II_29007_marnise
- **Access Level:** Public
- **Primary PDB:** ma_pdb_29007
- **User Account:** marnise_plsqlauca_29007
- **Submission Period:** February 2026
- **Repository URL:** [To be populated upon repository creation]
- ✅ Final Checklist 

 Correct PDB names used (exact naming conventions followed)

 User created inside the PDB

 Temporary PDB created successfully

 Temporary PDB deleted completely

 OEM dashboard screenshot included

 GitHub repository is set to PUBLIC

 README is clear, short, and professional

 Deadline respected

---

