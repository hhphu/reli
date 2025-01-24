# Scenario
We are enhancing our bid optimization process based on observed limitations with the current approach. The updated framework should address these challenges and improve advertising efficiency. We've observed Amazon performance varies based on time of day, leading us to implement different bidding strategies for specific time windows. Additionally, we noticed that Amazon target selection can lead to competition among targets with the same keyword text, impacting performance scores. To prevent cannibalization within the same group, we are adopting a strategy of having only one enabled target per group. Since we expect Amazon to group similar targets together when selecting what to advertise, we want to aggregate performance data for all targets in the same group (based on Short ID, Keyword Text, Match Type, Campaign Type). This ensures more accurate and cohesive bid adjustments.

## Time-Based Bidding Versions:

**1. Weekday_day:** Monday - Friday from 4 AM to 7 PM (not inclusive)

**2. Weekday_night:** Monday - Friday from 7 PM to 4 AM (not inclusive)

**3. Weekend_day:** Saturday - Sunday from 4 AM to 7 PM (not inclusive)

**4. Weekend_night:** Saturday - Sunday from 7 PM to 4 AM (not inclusive)
  
## New Requirements:
- Optimize bids based on keyword groups, which combine keywords with the same group_id (Short ID, Keyword Text, Match Type, Campaign Type).
- Apply bid optimizations at the version level (Weekday_day, Weekday_night, Weekend_day, Weekend_night) and aggregate performance metrics per version to capture time-based patterns.
    - Performance is now available at the hour level.
- Only apply optimizations to groups with at least 5 clicks.
- Calculate effective_bid using methods such as:
    - Average bid across all targets in the group.
    - Most common target in the group.
    - Bid from the highest-performing target.
    - Smallest or highest bid in the group.
    - Candidates should evaluate the pros and cons of each method and propose which approach is most suitable, considering scenarios where paused targets or outliers may influence results.

## Key Consideration:
- Apply bid updates to paused targets within affected groups by querying the keyword_multivers table to capture all targets.
- Save bid updates back into the database.

# TABLE OF CONTENTS
- [Test Plan Development]()
- [Bug Report Template]
- [Bug Report Workflow]
- [Test Case Design]
  
