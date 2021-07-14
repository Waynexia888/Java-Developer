### Interview Question: What is the difference between wait and sleep?
- sleep is a static method in the thread class, but wait must be declared in the object class. That is the major difference.
- you can write Thread.sleep(); but you can't write Thread.wait(), because it is an object level method, not class level static method.
