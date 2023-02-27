# job-scheduling-problem
def select_jobs(n, jobs):
    # sort the jobs based on their end time in ascending order
    jobs.sort(key=lambda x: x[1])
    
    max_profit = 0
    selected_jobs = []
    end_time = 0
    
    # iterate through the sorted list of jobs and select the ones with highest profit and no overlap
    for job in jobs:
        start_time, curr_end_time, profit = job
        if start_time >= end_time:
            selected_jobs.append(job)
            max_profit += profit
            end_time = curr_end_time
            
    # print the number of jobs left and the total earnings of the other employees
    remaining_jobs = n - len(selected_jobs)
    earnings = sum(job[2] for job in jobs if job not in selected_jobs)
    
    print("The number of tasks and earnings available for others")
    print(f"Task: {remaining_jobs}")
    print(f"Earnings: {earnings}")
    
#input
n = int(input("Enter the number of Jobs\n"))
jobs = []
for i in range(n):
    start_time = int(input("Enter job start time (in HHMM 24HRS format)\n"))
    end_time = int(input("Enter job end time (in HHMM 24HRS format)\n"))
    profit = int(input("Enter job earnings\n"))
    jobs.append((start_time, end_time, profit))

#output
remaining_jobs, remaining_earnings = job_scheduling(n, jobs)
print("The number of tasks and earnings available for others")
print("Task:", remaining_jobs)
print("Earnings:", remaining_earnings)
