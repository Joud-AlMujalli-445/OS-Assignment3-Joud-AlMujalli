# 📝 MY_WORK: Student Information, Development Log, Reflection & Answers

> This is the **only file** your instructor reads to grade Parts 3 and 4 (documentation and video). Everything you write here must be **in your own words**.

---

## 🛑 STOP: Read This Before You Do Anything Else

> ### 1️⃣ Read the whole `README.md` first
> The `README.md` in this repository contains the full instructions: how this assignment continues Assignment 1, the Chapter 5 recap, class descriptions, feature specifications, question prompts and the video script. **If you skip it, you will lose marks.**
>
> ### 2️⃣ Understand the full code before answering any question
> Open `SchedulerSimulationSync.java` and read it **from top to bottom**. You must be able to explain what `SharedStats`, `ReadyQueue`, `CpuWorker`, `RaceWindow.pause()`, `ReentrantLock` and `Semaphore` do **before** you write a single answer in Parts B and C. **Run the original starter first** (it is intentionally broken) and **save its output**: you need it for Question 1 of Part C.
>
> ### 3️⃣ Use only the code of this repository
> Work **only** on `SchedulerSimulationSync.java` from this repository. Do **not** copy or paste code from your previous assignments.
>
> ### 4️⃣ Commit many times, not once
> A single commit, or all commits made in the last hour, costs you **-0.5 mark**. See the [Commit Rules](#-commit-rules-mandatory) below.

**How to use this file:**
1. Fill in your **Student Information** (below) right now.
2. Follow the steps in the **Work Roadmap** in order.
3. Update the **Development Log** *every time* you work on the assignment, not at the end.
4. Do not delete any section header. Replace the `[...]` placeholders with your own text.

---

## 👤 Student Information

> ⚠️ **WARNING:** Fill this in first. Your name and ID must match the student ID you set in `SchedulerSimulationSync.java` (line 304) and the one you say in your video.

| Field | Your Answer |
|-------|-------------|
| **Full Name** | [Joud AlMujalli] |
| **Student ID** | [445052144] |
| **University Email** | [445052144]@std.psau.edu.sa |
| **GitHub Username** | [Joud-AlMujalli-445] |
| **Repository Link** | [https://github.com/Joud-AlMujalli-445/OS-Assignment3-Joud-AlMujalli] |
 
---

## 🎥 Video Link

**Video Link**: [Paste your video link here]

> ⚠️ **WARNING:** The video must be **publicly accessible** ("Anyone with the link can view") on **Google Drive**, **YouTube (Unlisted or Public)** or any other cloud file-sharing system. A private, restricted or broken link counts as a **missing video (-1 mark)**.
>
> 💡 **TIP:** Open the link in a **private/incognito window** before you submit. If it asks you to log in or request access, it is not public.
>
> 📌 **NOTE:** The link goes in **this file only** (`MY_WORK.md`), **not** in `README.md`. Name your video file `StudentID_Assignment3_Demo.mp4`. It must last **2 to 3 minutes**.

---

## 🗺️ Work Roadmap (follow in this order)

| Step | What to do | Where | Marks |
|:----:|------------|-------|:-----:|
| 0 | Read `README.md`, read the full code, **run the original starter and save its output** (it fails on purpose) | Your IDE | – |
| 1 | Fork, rename, keep the repo **PUBLIC**, set your student ID (line 304), **commit** | GitHub + code | Part 1 (1) |
| 2 | Feature 1: Mutex lock on the ready queue, **commit** | Code | Part 2 (0.25) |
| 3 | Feature 2: Mutex lock(s) on the shared statistics, **commit** | Code | Part 2 (0.25) |
| 4 | Feature 3: Counting semaphore instead of busy waiting, **commit** | Code | Part 2 (0.5) |
| 5 | Development Log (5+ entries, different dates) | This file, Part A | Part 3 (0.5) |
| 6 | Reflection (4 questions) | This file, Part B | Part 3 (0.5) |
| 7 | Technical Answers (4 questions) | This file, Part C | Part 3 (0.5) |
| 8 | Record the video, upload it, paste the link above | Video + this file | Part 4 (1.5) |
| 9 | Final check, then submit the repo link on Blackboard | Blackboard | – |

> 💡 **TIP:** Tick each step off as you go. Do not leave the log, the reflection or the video for the last day.

---

## 🔁 Commit Rules (MANDATORY)

> ### ⚠️ MANY COMMITS ARE REQUIRED. A single bulk commit is penalized (-0.5 mark).

**Minimum: 4 meaningful commits. Aim for 7 or more.**

| # | Commit | Example message |
|:-:|--------|-----------------|
| 1 | Student ID set | `Set my student ID: 441234567` |
| 2 | Feature 1: Ready queue lock | `Feature 1: Protected the ready queue with a ReentrantLock` |
| 3 | Feature 2: Statistics locks | `Feature 2: Added locks to the shared statistics counters` |
| 4 | Feature 3: Semaphore | `Feature 3: Replaced busy waiting with a counting semaphore` |
| 5 | Development log entries | `Docs: Added development log entries 1-3` |
| 6 | Reflection and answers | `Docs: Completed reflection and technical answers` |
| 7 | Video link | `Docs: Added demo video link` |

**Rules:**
- ✅ **One commit per feature.** Do not put all three features in one commit.
- ✅ **Commit after each work session**, and after each part of this file.
- ✅ **Spread your commits over different dates.** Not all in one day.
- ❌ **Do not make all commits in the last hour** before the deadline (November 14, 2026).
- ❌ **No vague messages** like `done`, `update` or `final version`.

> 💡 **TIP:** Your commit history is checked and you **show it in your video** (at least 4 commits visible). Your development log dates should match your commit dates.
>
> 💡 **TIP:** **Use VS Code** (see *Recommended Development Environment* in `README.md` for the full setup). Sign in to GitHub in VS Code, then commit from the Source Control panel (Ctrl+Shift+G) → stage → write a message → Commit → Sync/Push. You can edit and commit this file the same way. **Pushing** matters: commits that are not pushed to GitHub are invisible to the instructor.

---

# Part A: Development Log (0.5 mark)

> ⚠️ **WARNING:** Minimum **5 entries**, spread over **different dates**. Five entries written on the same day, or written all at once at the end, will lose marks and look like a copy. Entry dates should be **between the start of the assignment and the deadline (November 14, 2026)**.
>
> 💡 **TIP:** Write an entry at the **end of each work session**, while you still remember what happened. It takes 5 minutes.
>
> 💡 **TIP:** Be specific. "Worked on the code" is a weak entry. "Added a `ReentrantLock queueLock` to `ReadyQueue` and wrapped the body of `poll()` in `lock()` / `try` / `finally { unlock() }`" is a strong one.
>
> 📌 **NOTE:** Each entry needs: date and time, what you did, details, challenges, solution, and time spent. Real challenges are fine (and expected). Do not invent fake ones.

## Example Entry (do not copy it, write your own)

### Entry 1 - [November 2, 2026, 4:30 PM]
**What I did**: Forked the repository, set my student ID, and ran the original starter

**Details**:
- Forked the starter repository and renamed it
- Changed student ID on line 304 to my actual ID (441234567)
- Ran the original program: 4 CPUs started, three of them picked `P1`, then `IllegalThreadStateException` and the watchdog stopped the program
- Saved the output in a text file for 
- Committed and pushed: `Set my student ID: 441234567`

**Challenges**:I did not understand why the same process was picked by three CPUs

**Solution**: Read `ReadyQueue.poll()` again and found the `RaceWindow.pause()` between reading the head and removing it

**Time spent**:45 minutes

---

## Your Development Log

### Entry 1 - [November 11, 2026, 7:30 PM]
**What I did**:
Set up my GitHub repository and development tools.
**Details**:
- Forked the starter repository, renamed it to OS-Assignment3-Joud-AlMujalli, and kept it public
- Installed JDK, Git and VS Code, and linked VS Code to my university GitHub account
- Cloned my repository and set my student ID on line 304
- Committed and pushed: "set my student ID"

**Challenges**:
  The JDK installer had JAVA_HOME disabled by default, and I was not sure which options to select.

**Solution**:
I enabled the PATH and JAVA_HOME options, then checked the installation with java -version.

**Time spent**:
30 minutes

---

### Entry 2 - [November 12, 2026, 2:30 PM]
**What I did**:
Ran the original broken starter and saved its verification block.

**Details**:
- The starter crashed with a NullPointerException in ReadyQueue.snapshot() (line 153), thrown from CpuWorker.run()
- The verification block showed expected 42 / 20 / 127836 but observed 0 for all three counters, because all 4 CPUs crashed
- Pasted the verification block into MY_WORK.md (Question 1) and committed it
- 
**Challenges**:
The VS Code terminal crashed with a PSReadLine error after I pressed Ctrl+C and other keys while the program was running.

**Solution**:
I closed the terminal, ran the program again, and only used Ctrl+C after selecting text.

**Time spent**:
1 hour

---

### Entry 3 - [November 12, 2026, 6:30 PM]
**What I did**:Feature 1, protected the shared ready queue with a ReentrantLock.

**Details**:
- Added one ReentrantLock (queueLock) protecting both list and map
- Used lock() + try/finally in add(), poll(), processOf() and snapshot()
- Kept the return statements inside the try block so finally always unlocks
- Committed: "protected the ready queue with a ReentrantLock"

**Challenges**:
The code showed many red errors after my edit, and I thought it was in a different part of the code.

**Solution**:
I checked the Problems panel and the brackets of each method, then ran the program several times: no more exceptions.

**Time spent**:
45 minutes

---

### Entry 4 - [November 13, 2026, 1:00 AM]
**What I did**:
Feature 2, protected the three shared statistics counters.

**Details**:
- Used one lock per counter (contextSwitchLock, completedProcessLock, serviceTimeLock) because the counters are independent
- Protected the 3 update methods and the 3 getters, always with try/finally
- Committed: "Feature2 Added locks to the shared statistics counters"
- 
**Challenges**:
Java showed "cannot be resolved" because my lock was declared as Completedprocesslock but used as completedLock. Later a WATCHDOG appeared in the second run.

**Solution**:
I used the same name everywhere. The WATCHDOG came from an unlock() that was not correctly inside finally; after fixing it, all runs passed.


**Time spent**:
1 hour & 30 minutes

---

### Entry 5 - [November 13, 2026, 2:45 AM]
**What I did**: 
Feature 3, replaced busy waiting with a counting semaphore.

**Details**:
- Added Semaphore readyCount with initial value 0 in ReadyQueue
- add() calls release() after adding the process; CpuWorker.run() calls acquire() before poll()
- The CPU that sees completed == total calls release(totalCPUs) so the blocked CPUs wake up and stop
- Verification: 42 / 20 / 127836 all correct and Busy-waiting polls = 0
- Committed: "Feature 3: Replaced busy waiting with a counting semaphore" and removed the old TODO comments
- 
**Challenges**:
The push failed with "Could not resolve host: github.com" because the internet was down.

**Solution**:
   I waited for the connection to come back and pressed Sync Changes again; all commits are now on GitHub.
   
**Time spent**:
1 hour & 15 minutes

---

### Entry 6 - [Optional - Date and Time]
**What I did**:

**Details**:

**Challenges**:

**Solution**:

**Time spent**:

---

## Development Log Summary

> 💡 **TIP:** Fill this in **last**, after all entries are written.

**Total time spent on assignment**: [5 hours]

**Most challenging part**:
Understanding why a lock that is not released causes the program to hang. After Feature 2, the WATHDOG appeared because one unlock() was not correctly inside a finally block, so the other CPUs waited forever. The semaphore shutdown in Feature 3 was also hard, because the CPUs blocked on acquire() never wake up unless the last CPU calls release(totalCPUs).

**Most interesting learning**:
A simple count++ is really three steps (read, add, write), so two CPUs can lose an update, and this bug does not appear in every run. I also learned that a semaphore lets a CPU sleep until a process is available instead of polling, so Busy-waiting polls became 0.

**What I would do differently next time**:
I would start earlier and spread the work over more days. I would run the program at least five times after every change, and write the development log during the work instead of afterwards.

---

# Part B: Reflection (0.5 mark)

> 🛑 **STOP:** Do **not** start this part until you have read the `README.md`, read the **entire** `SchedulerSimulationSync.java`, run it, and finished the three features.
>
> ⚠️ **WARNING:** Each answer must be **5 to 7 sentences**, in **your own words**. Copied or AI-generated answers without understanding get **0 marks for the whole assignment**. You may be asked to explain them in person.
>
> 💡 **TIP:** Mention concrete things you actually did: a method you wrote, an error you hit, a line of output you saw. Generic answers score low.
>
> 💡 **TIP:** Draft your answer in a few bullet points first, then turn them into sentences.

## Question 1: What did you learn about synchronization?

> 💡 **TIP:** Talk about race conditions (read-modify-write), critical sections, mutual exclusion with `ReentrantLock` and `try/finally`, the role of a counting semaphore, and what surprised you when the starter failed.

**Your Answer:** *(5-7 sentences)*

[I learned that a race condition happens when several threads read and change the same shared data, because count++ is really three steps: read, add, and write. When I ran the starter, the four CPUs crashed with a NullPointerException in ReadyQueue.snapshot(), so I saw that even reading a shared list without a lock is unsafe. I fixed this with a ReentrantLock and always released it in a finally block, so the lock is freed even if an exception happens. A critical section needs mutual exclusion, which means only one CPU can change the queue or a counter at a time. I also learned that a counting semaphore that starts at 0 lets a CPU sleep on acquire() until a process is added, instead of checking an empty queue again and again. What surprised me most was that all three counters were 0 in the starter, because the queue bug crashed the CPUs before they updated anything.]

## Question 2: What was the most challenging part of this assignment?

> 💡 **TIP:** Pick **one** specific challenge (understanding why the starter failed, choosing the lock granularity, the initial value of the semaphore, the shutdown of the CPUs, Git, the video) and say *why* it was hard.

**Your Answer:** *(5-7 sentences)*

[The most challenging part was understanding why my program showed a WATCHDOG message after Feature 2. The output stopped after "CPU-2 picks P5", and nothing else was printed for about 34 seconds. At first I did not know if it was a lost update or a different problem. The cause was a lock that was not released correctly, because one unlock() was not inside a finally block, so the other CPUs waited forever. This was hard because there was no error message, the program just froze. After I fixed it, I understood why every unlock() must be inside finally, and all my runs passed.]

## Question 3: How did you overcome the challenges you faced?

> 💡 **TIP:** Describe your method: reading the slides and the documentation, adding `System.out.println` to debug, running the program many times, re-reading the README, testing after each small change, asking for help.

**Your Answer:** *(5-7 sentences)*

[I worked in small steps and tested after every change. I followed the order in the README: first the queue lock, then the statistics locks, then the semaphore. After each feature I ran the program several times and only committed when the verification block was correct. When Java showed "cannot be resolved", I compared the names letter by letter and found that I wrote Completedprocesslock in one place and completedLock in another. For the watchdog problem, I checked that every lock() had an unlock() inside a finally block. I also asked for explanations when I did not understand a concept, and then I checked my code again with the verification block.]

## Question 4: Where can synchronization concepts be applied in real-world applications?

> 💡 **TIP:** Use real applications you know (banking and money transfers, ticket or seat booking, a shared counter on a website, a print queue, a database) and connect each one to what you built here (shared data, critical section, lock or semaphore).

**Your Answer:** *(5-7 sentences)*

[In banking, two transfers that update the same account at the same time can lose an update, just like my lost update on contextSwitchCount. In ticket or seat booking, a lock makes sure two customers cannot reserve the same seat, which is the same critical-section problem as two CPUs taking the same process from my ready queue. A print queue works like my ReadyQueue: programs add jobs and the printer takes them one by one, and a semaphore can let the printer sleep until a job arrives instead of busy waiting. A visitor counter on a website needs a mutex so that no increment is lost, like my shared counters. Databases also use locks to keep data correct when many users write at the same time. In all these cases the idea is the same as in my assignment: protect shared data with a lock and avoid busy waiting.]

### Optional: What would you like to learn more about?

[Any topics related to synchronization or operating systems that you're curious about?]

### Optional: How confident do you feel about synchronization concepts now?

[Beginner / Intermediate / Confident. What do you understand well? What needs more practice?]

### Optional: Feedback on the assignment

[Any comments? Was it helpful? Too easy or hard? Suggestions?]

---

# Part C: Technical Answers (0.5 mark)

> 🛑 **STOP:** You cannot answer these questions without understanding the code. Re-read `SchedulerSimulationSync.java` and **run it** first. Your answers must reference **your own code and your own output** (your student ID makes your output and your expected values unique).
>
> ⚠️ **WARNING:** Each answer must be **3 to 5 sentences**, with specific examples from your code or output. Use correct terms: race condition, critical section, mutual exclusion, mutex lock, semaphore, busy waiting, deadlock, producer, consumer.
>
> 💡 **TIP:** Keep the output of the **original starter** and the output of your **final version** in text files or screenshots, so you can copy real snippets for Question 1.

## Question 1: Race Condition in Your Own Output

**Question**: Run the **original starter** (before any fix) and paste the **verification block** of that run. Which value was wrong (expected vs observed)? Explain **step by step**, with two named threads/CPUs, how **one lost update** happens on one of the shared variables (read, `RaceWindow.pause()`, write). Why can the same bug happen on a real machine even without `RaceWindow`, and why is it hard to detect?

> ⚠️ **WARNING:** The snippet must come from **your own run** (with your student ID), not from a classmate or from this README.
>
> 💡 **TIP:** Use a small timeline: *CPU-1 reads `contextSwitchCount` = 12 → CPU-2 reads 12 → CPU-1 writes 13 → CPU-2 writes 13 → one increment is lost.* If your starter run crashed before printing numbers, run it several times (or paste the exception and the watchdog message and explain it).

**Your Answer:** *(3-5 sentences)*


  
Verification block of the **original starter**:
```
[═══ VERIFICATION (expected values are computed from YOUR seed) ═══
  Context switches (quanta executed)   expected 42      observed 0   ✘ MISMATCH
  Completed processes                  expected 20      observed 0   ✘ MISMATCH
  Total service time (ms)              expected 127836  observed 0   ✘ MISMATCH
  Busy-waiting polls (must be 0)       expected 0       observed 0   ✔
  ✘ At least one check failed: a race condition or busy waiting is still present.]
```

Verification block of **my final version**:
```
[═══ VERIFICATION (expected values are computed from YOUR seed) ═══
Context switches (quanta executed) expected 42 observed 42 ✔
Completed processes expected 20 observed 20 ✔
Total service time (ms) expected 127836 observed 127836 ✔
Busy-waiting polls (must be 0) expected 0 observed 0 ✔
✔ All shared values are consistent. ]
```

**Explanation of the timeline:**
[In my starter run, all three counters were wrong by their full expected value: 42, 20 and 127836 were expected, but 0 was observed. The zeros appeared because the four CPUs crashed with a NullPointerException in ReadyQueue.snapshot() before they updated any counter. A lost update on contextSwitchCount happens like this: CPU-1 reads 12, RaceWindow.pause() delays it, CPU-2 also reads 12, CPU-1 writes 13, and then CPU-2 writes 13 too, so two quanta ran but the counter increased only once. On a real machine the same bug can happen without RaceWindow, because count++ is three steps (read, add, write) and the OS can stop a thread between any two of them, or two cores can run them at the same time. It is hard to detect because it depends on timing, so it appears only in some runs. ]

## Question 2: Critical Sections and Lock Granularity

**Question**: List the **critical sections** you protected (variables and methods) and the lock(s) you used. **Lock granularity:** did you use **one lock** for the three statistics or **one lock per variable**? Why, and what is the trade-off? Why is the **ready queue** protected by a **different** lock than the statistics? Explain how your solution provides **mutual exclusion**, and discuss **progress** and **bounded waiting** (a default `ReentrantLock` is not fair: what does that imply?).

> 💡 **TIP:** The three counters are independent: does updating `contextSwitchCount` need to block an update of `totalServiceTime`? Also think about what could go wrong (deadlock, or long waiting) if the queue lock and the statistics lock were the **same** lock and a thread held it while doing something slow.

**Your Answer:** *(3-5 sentences)*

I protected the ready queue (list and map) with queueLock in add(), poll(), processOf() and snapshot(), and the three counters with one lock each: contextSwitchLock, completedProcessLock and serviceTimeLock. I used one lock per counter because the counters are independent, so a CPU updating totalServiceTime does not need to wait for a CPU updating contextSwitchCount; the trade-off is more locks to manage, but less waiting than one global lock. The queue has a different lock because it is a different shared structure, and if both used the same lock, a thread holding it during a slow operation would block all the other CPUs for no reason. Each lock gives mutual exclusion because only one thread can be between lock() and unlock(), and progress is kept because unlock() is always in finally. A default ReentrantLock is not fair, so bounded waiting is not guaranteed: a CPU could wait a long time while others keep taking the lock, although this did not happen in my runs.

| Critical section (variable / method) | Lock used | Why it needs protection |
|---|---|---|
|ReadyQueue.add(), poll(), processOf(), snapshot() (list, map)|queueLock|Two CPUs could read the same head, or the list could change while another CPU reads it|
|incrementContextSwitch(), getContextSwitchCount() | contextSwitchLock | Read-modify-write on contextSwitchCount can lose an update |
|incrementCompletedProcess(), getCompletedProcessCount() | completedProcessLock | A lost update would stop the CPUs from detecting the end |
|addServiceTime(), getTotalServiceTime() | serviceTimeLock | Read-modify-write on totalServiceTime can lose an update |


## Question 3: Busy Waiting vs Semaphore

**Question**: Describe the **busy waiting** of the starter and its cost (give the `Busy-waiting polls` number from your **starter** run). What does the **value of your semaphore** represent? What is its **initial value** and why? What is its value right after the `numProcesses` initial `add()` calls? Why does the last CPU call `release(totalCPUs)` at the end, and what would happen if it did not?

> 💡 **TIP:** Think about what a CPU does when the queue is empty in the starter, and what a CPU does in your final version (is it running, ready or blocked?). Also check what happens to a CPU blocked in `acquire()` when no process will ever be added again.

**Your Answer:** *(3-5 sentences)*

In the starter, a CPU that found the queue empty slept 20 ms and polled again, which is busy waiting that wastes CPU time; in my starter run Busy-waiting polls was 0 only because the CPUs crashed before reaching that loop. In my final version the value of the semaphore readyCount represents the number of processes waiting in the ready queue, and its initial value is 0 because the queue is empty at the start. Right after the 20 initial add() calls its value is 20, and each acquire() before poll() decreases it by one. The last CPU calls release(totalCPUs) so every CPU blocked in acquire() wakes up, sees that all processes are completed, and stops. Without it, those CPUs would stay blocked forever on an empty queue, and the program would hang until the watchdog stopped it.

## Question 4: Classical Problems and Deadlock

**Question**: The CPUs and the ready queue look like a classical synchronization problem of Chapter 5. **Name it**, and say who plays the **producer** and the **consumer** roles (careful: here the CPUs also re-enqueue processes). If the ready queue were **bounded** (capacity `K`), name the **three semaphores** you would need and their **initial values**. Describe a **deadlock scenario** that appears if a thread acquired the **mutex before** waiting on the semaphore (or if two locks were acquired in different orders), and say **which of the four necessary conditions** you would break to prevent it.

> 💡 **TIP:** Recall the bounded-buffer solution of the slides (`empty`, `full`, `mutex`) and the order of `wait()` calls in the producer and the consumer. For the deadlock, think about a producer that holds the mutex while waiting for a free slot that only a consumer (who needs the mutex) can create.

**Your Answer:** *(3-5 sentences)*

**Classical problem and roles**:
It is the producer-consumer (bounded-buffer) problem. The producers are main, which adds the 20 initial processes, and the CPUs that put an unfinished process back with add(); the consumers are the CPUs that take a process with poll().


**Semaphores for a bounded queue (name and initial value)**:
mutex = 1 (mutual exclusion on the queue), empty = K (free slots, K is the capacity), and full = 0 (processes in the queue, like my readyCount).

**Deadlock scenario and prevention**:
If a producer takes the mutex before wait(empty) and the queue is full, it waits for a free slot while holding the mutex. A consumer needs the mutex to remove a process and free a slot, so both wait forever: deadlock. I would break the hold-and-wait condition by calling wait(empty) first and taking the mutex only after it, so no thread waits while holding the lock.

## Summary

**Key concepts I understood through these questions:**
1. A race condition is a lost update on shared data, and count++ is really three steps (read, add, write).
2. A mutex lock gives mutual exclusion, and unlock() must always be inside finally.
3. A counting semaphore lets a thread sleep instead of busy waiting, and it needs a shutdown signal like release(totalCPUs).

**Concepts I need to study more:**
1. Fair locks and bounded waiting (starvation).
2. The four necessary conditions of deadlock and how to prevent each one.

---

# ✅ Final Checklist (complete before submitting)

> ⚠️ **WARNING:** Go through every line. Blackboard does not accept submissions after the deadline, which is **November 14, 2026**.

**Repository**
- [x] Repository is **PUBLIC** (Settings → Danger Zone → Visibility)
- [x] Repository is renamed to `OS-Assignment3-YourFirstName-YourLastName`
- [x] GitHub account uses the university email (`@std.psau.edu.sa`)

**Code**
- [x] Student ID is set in `SchedulerSimulationSync.java` (line 304)
- [x] My code is based **only** on the starter of this repository (nothing copied from previous assignments)
- [ ] Code compiles and runs with no errors, and terminates by itself (no `⛔ WATCHDOG`)
- [x] Feature 1 (ready queue lock), Feature 2 (statistics locks) and Feature 3 (semaphore, no busy waiting) all work
- [x] **The four verification lines are ✔ in 5 consecutive runs**
- [x] Every lock is released in a `finally` block
- [ ] `RaceWindow`, `Config`, the verification block and the watchdog are **unchanged**
- [x] Each feature has clear comments

**Commits**
- [x] **At least 4 meaningful commits, ideally 7 or more**
- [x] **One commit per feature**
- [x] Commits are spread over **different dates** (not all in the last hour)
- [x] Everything is **pushed** to GitHub

**This file (`MY_WORK.md`)**
- [x] Full name and student ID filled in at the top
- [x] Development log has **5+ entries** on different dates
- [x] Reflection: 4 questions, 5-7 sentences each
- [x] Technical answers: 4 questions, 3-5 sentences each, with examples from **your** output (starter output **and** final output pasted in Question 1)
- [x] No `[...]` placeholders left
- [x] No section headers deleted

**Video**
- [x] 2-3 minutes long, named `StudentID_Assignment3_Demo.mp4`
- [x] Shows your name, ID, repository, 3 features (and your lock granularity choice), IDE execution with the verification block, one synchronization concept, and commit history
- [x] Link is **public** (tested in an incognito window) and pasted in the **Video Link** section above

**Blackboard**
- [x] Submit **only** the link to your public GitHub repository

> 🎯 **Good luck!** Start early, commit regularly, and make sure you can explain every line you submit.
