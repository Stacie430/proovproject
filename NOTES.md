# What I checked, and what the agent got wrong

I reviewed the changes file by file instead of trusting the first agent answer.  
I compared the logic against the task rules (15,000 km interval and 80% threshold) and checked behavior with tests and verification output.

## What the agent got wrong

The first pass missed an important test case around missing odometer readings in the fleet report flow.  
I noticed this by reading the failing/expected test scenarios and checking that one required case was still not covered.

## What I checked before I accepted its work

I ran the test suite and the repository verification script to confirm the fixes were real and complete.  
I specifically checked that:

- nearly worn cars are flagged correctly,
- cars with missing last-service readings are not falsely flagged,
- report generation handles cars with missing readings without crashing,
- the 80% rule and service interval stayed unchanged.

## What the data actually said

The analysis showed that not every obvious feature is a strong predictor on its own.  
In particular, high total mileage alone was not enough to separate breakdown vs. non-breakdown cars reliably, so the risk signal had to come from the combined factors in the dataset.
