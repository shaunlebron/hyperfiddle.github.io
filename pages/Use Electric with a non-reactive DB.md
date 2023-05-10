- Discussions
	- https://clojurians.slack.com/archives/C7Q9GSHFV/p1682786697009099
	- [SQL data backend](https://gist.github.com/dustingetz/1960436eb4044f65ddfcfce3ee0641b7)
- Probably the long term solution is to integrate the router to refresh queries on navigate, and also refresh queries on a configurable timer (say 60 seconds), and force opt-in to get realtime refresh on a custom event for specific realtime regions of the app. The custom event could be on every pg_notify, or hopefully for realtime chat views we are using a document database designed to support realtime collection subscriptions (i.e. not sql)
- Problems
	- "messy query refresh problem"
		- idea: use command pattern to get clear events which can be used to trigger queries?
			- No, i don’t see how a command pattern solves the messy query refresh problem, in the worst case someone can make a one off edit via pgadmin gui and your queries need to refresh, in the best case where you just promise to only write via commands you can probably inspect the transaction to decide which views to query
		-