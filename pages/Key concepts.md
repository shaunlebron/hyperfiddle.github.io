- reactivity graph
  collapsed:: true
	- The key things I need to get is this with Electric Clojure being reactive and this DAG.
	- Of course, they seem to be very interconnected, it is the DAG that makes EC reactive.
	- When I look at a piece of EC code I am actually looking at the DAG, the EC compiler builds the DAG from that code.
	- Then it knows where in the graph each piece of (reactive) data flows.
	- At run time, if some source of data has new content, each place in the DAG where this data is used can be updated.
	- The reaction is the result of a push, rather than a pull, and it is pushed only via the paths through the graph where there are things that need to react.
	- If I squint I can see a the signal as it travels through the DAG. It looks like a bolt of lightning. Is this why it is called Electric Clojure?
- client/server transfer
- everything is async
  collapsed:: true
	- That everything is reactive also means that it all is async.
	- A call to a function will always be waiting. Is this true?
	- And is it true even when the call is made to some piece of code that does not deal with any reactive data?
	- Say (* (+ 1 2) 3). Will the * call be ”waiting” for the + to be ready?
	- Or is it normal Clojure semantics there, that the inner function will be evaluated and then the outer, and there is no waiting going on?
- missionary
  collapsed:: true
	- stream, signal
- it's a compiler
  collapsed:: true
	- Evaluating a piece of electric code does not run it, right? It compiles it.
	- So, in the editor, if I would evaluate som form inside an , it only compiles it.