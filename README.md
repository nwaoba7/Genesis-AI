Interactive Self-Learning AI in Python (Python 2.7)
======================
This is an AI made in Python.  
Because it is a self-learning type, it learns words on its own and speaks about various things by combining the words it has learned.

You can have it read sentences in advance as morpheme candidates, or you can have it learn from nothing, based only on the sentences you input.

How to Use
------
### Talking with the AI ###
Let's try talking with the AI!

Please prepare an empty file called `` save/alice.txt ``. Of course, this must be writable.  
Then move to the `` AI/ `` folder and run it like `` python Alice_AI.py ``.  
Once it has loaded `` save/alice.txt ``, it will display something like `` Aliceさんがログインしました `` ("Alice has logged in"), so please continue by typing something after `` You: ``.

There is no particular command prepared for exiting, so please exit using something like `` Ctrl + C ``.

 
### Having AI talk with AI ###
Next, let's have AI talk with AI!

Please prepare two empty files called `` save/alice_2.txt `` and `` save/bob_2.txt ``. Of course, these must be writable.
Just as before, run it in the `` AI/ `` folder like `` python ai2ai.py ``.
Once the messages `` Aliceさんがログインしました `` ("Alice has logged in") and `` Bobさんがログインしました `` ("Bob has logged in") appear, the AIs will talk automatically from there!
 

### Having it read a file in advance ###
You can also have it read a file in advance. In that case, you need to break down the sentences written in the file into morphemes beforehand.  
First, let's prepare a file (some files I pulled from Aozora Bunko are in the `` text/ `` folder).

Next, run this as `` python Cutmorph.py [filename] ``.  
Then it will become something like `` save/m_[filename].txt `` (if it was originally a text file, it becomes `` ~.txt.txt ``).

After that, if you rename this to something like `` alice.txt `` or `` bob_2.txt `` as above and run the AI, it will automatically create conversations by itself from the original sentences! It might be interesting to have the AI imitate a favorite character or something.


### When using Twitter logs ###
If you want to have the AI speak using Twitter logs, it seems fastest to bring the logs from [twilog](http://twilog.org/).  
You can download a CSV file with an appropriate character encoding from the twilog management page. Since development is currently done entirely in utf-8, please download it in utf-8.

Once you have the log file ready, run it as ``python text/non_number.py [log file]``. Unnecessary numbers and so on will be removed from the log file, and it will come out in the form of ``[log file].txt``.

After that, if you have the AI read this in the same way as above, using something like ``python Cutmorph.py [[log file].txt]``, you can have conversations with it through the Twitter logs.


Modifying the Program
------- 

### Changing the file to load ###
The setting for the file to be loaded first, in the case of `` ./Alice_AI.py ``, is at the very bottom,

```python
if __name__ == "__main__":
    alice = AliceEngine("save/alice.txt") # ← Here
    while True:
        input = raw_input("You：").decode('utf-8')
        if input == '': continue
        alice.mainloop(input)
```

In the case of ``./ai2ai.py``, it is around the middle,

```python
AI.append(Alice_AI.AliceEngine("save/alice_2.txt",u"Alice"))  # ← Here
AI.append(Alice_AI.AliceEngine("save/bob_2.txt",u"Bob"))      # ← Here
```

so please change the filenames in these appropriately.


-------
Have a fun AI life!  
Please note that this program uses python2.7.3. There are parts that will not work in the python3.x series, so please understand this in advance (in that case, please feel free to fork and modify it appropriately!).
