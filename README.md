# Production-Planning

Case Situation: We cooperate with a animal food manufacturer, and they have limited storage space and is trying to maintain minimun inventort on-hand.
So our task is to build a model for them to calculate when should they issue purchase orders.

#Process data
"Process": Process name
"Prerequisite": processed needed to be done before starting this process
"Duration": How many days this task takes

For example

![image](https://user-images.githubusercontent.com/58899897/194221480-25f60155-a62b-4289-a332-3a114a6b8890.png)

Let's use python to create a directed graph to have a quick understanding of the processes

![image](https://user-images.githubusercontent.com/58899897/194221788-78aeb6df-721d-4ead-b0d2-ea0e97e8dd4e.png)

If the process flows are complicated, the graph may be difficult to understand. To solve this issue, we could use different layout methods or try to manually edit pos.

# Algorithms
We use BFS & Critical Path algorithms to solve this issue
![image](https://user-images.githubusercontent.com/58899897/194223084-0fe2d9aa-42ed-4e8c-8e13-91960ae429ec.png)


#Result
How should we determine when and what amount of material should we order?
We could use the amount required minuses the total amount of inventory on-hand 
*we should order: required amount-(on-hand + in-transit)
We could use Slack to determin when should we order. If there is a positive slack, we could order later, thereby avoiding the shortage of storage space.
If there is a lead time for ordering raw material, we just need to add lead with the Duration.

"ES": Earliest Start
"EF": Earliest Finish
"LF": Latest Finish
"LS": Latest Start
"SK": Slack, how much time you could delay without violation of deadline.

![image](https://user-images.githubusercontent.com/58899897/194224785-f3b11c84-cbd2-449a-876e-7b19447c2b00.png)
For example, we could order the material of C and I later without the violation of deadline

