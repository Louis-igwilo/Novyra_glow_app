Glow-Up App — Data Model
1. Overview
This data model defines how the Glow-Up App stores user goals, tasks, schedules, and AI-driven adjustments. It supports an adaptive system that dynamically updates user plans based on behaviour and progress.
2. Database Tables
User
user_id (PK) 
name 
email 
wake_time 
sleep_time 
timezone 
created_at 

 Goal
goal_id (PK) 
user_id (FK → User) 
title 
category 
start_date 
end_date 
priority_level 

 Task
task_id (PK) 
goal_id (FK → Goal) 
title 
description 
duration_minutes 
frequency 
preferred_time 
difficulty_level 
Scheduled_Task
schedule_id (PK) 
user_id (FK → User) 
task_id (FK → Task) 
scheduled_date 
scheduled_time 
status 
completion_time 
AI_Adjustment_Log
ai_log_id (PK) 
user_id (FK → User) 
original_schedule_id (FK → Scheduled_Task) 
adjusted_schedule_id (FK → Scheduled_Task) 
reason 
confidence_score 
created_at 
Progress_Tracker
progress_id (PK) 
user_id (FK → User) 
goal_id (FK → Goal) 
completion_rate 
streak_count 
last_updated  

3. Relationships
One User → many Goals 
One Goal → many Tasks 
One Task → many Scheduled Tasks 
One User → many Scheduled Tasks 
One User → many AI Adjustment Logs 
One Goal → one Progress Tracker 

System Structure
User
 ├── Goal
 │     ├── Task
 │     │     └── Scheduled_Task
 │     └── Progress_Tracker
 └── AI_Adjustment_Log

4. AI Behaviour Logic
The AI system monitors user behaviour and adjusts schedules dynamically by:
Tracking completed vs missed tasks 
Detecting overload or fatigue patterns 
Rescheduling tasks intelligently 
Prioritising high-impact goals 
Improving future schedules using historical data 
5. Summary
This data model enables an adaptive productivity system where schedules evolve based on user behaviour, improving consistency and goal achievement over time.

