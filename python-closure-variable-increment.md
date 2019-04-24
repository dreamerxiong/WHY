
Situation 1:
<pre>
def foo():
    counter = [1]
    def bar():
        counter = counter + [1]
        print(counter)
    return bar
</pre>
<pre>
>>> foo()() 
Traceback (most recent call last):
  File "<input>", line 1, in <module>
  File "<input>", line 4, in bar
UnboundLocalError: local variable 'counter' referenced before assignment
</pre>

Situation 2:
<pre>
def foo():
    counter = [1]
    def bar():
        counter.append(1)
        print(counter)
    return bar
</pre>
<pre>
>>> foo()()
[1, 1]
</pre>

Situation 3:
<pre>
def foo():
    counter = [1]
    def bar():
        counter1 = counter + [1]
        print(counter1)
    return bar
</pre>
<pre>
>>> foo()()
[1, 1]
</pre>


## Reference:

https://stackoverflow.com/questions/21959985/why-cant-python-increment-variable-in-closure

### FIXME：
Difference between `counter = counter + [1]` , `counter.append(1)` and `counter1 = counter + [1]`