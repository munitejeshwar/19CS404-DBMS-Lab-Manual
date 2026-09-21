# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1100" height="662" alt="Screenshot 2026-09-08 140941" src="https://github.com/user-attachments/assets/ad036d12-250e-4c40-b316-fa57b11b3b67" />


### Entities and Attributes

<img width="1105" height="372" alt="Screenshot 2026-09-08 140959" src="https://github.com/user-attachments/assets/dfef9204-a1df-4e2e-8595-9ef0267fbd40" />


### Relationships and Constraints

<img width="1107" height="377" alt="Screenshot 2026-09-08 141020" src="https://github.com/user-attachments/assets/11acf043-099e-4749-8380-2b5bcedc4688" />


### Assumptions
- Each session involves exactly one trainer and one member.
- Programs are predefined (Yoga, Zumba, Weight Training, etc.).
- Payments are only for membership or session bookings.
---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
