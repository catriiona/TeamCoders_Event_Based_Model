# 5_Git_Commit_History
# Version control and how to track commits

Using **git log** we can see the commits we have created
```bash 
git log 
```
**Output**
```bash 
commit cebdb2ced222527abc2b062c804487e9c179bc6c (HEAD -> main)
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 12:32:43 2022 +0000

    first changes

commit f50fddc8b03956ce453375c1cf5d5799e5ce7a51
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 12:25:09 2022 +0000

    write ingredients
```
Your output will differ from the above not only in the date and author fields but in the alphanumeric sequence (hash) at the start of each commit.

- We can browse the development and access each state that we have committed.
- The long hashes following the word commit are random and uniquely label a state of the code.
- Hashes are used when comparing versions and going back in time.
- If the first characters of the hash are unique it is not necessary to type the entire hash.
- Output is in reverse chronological order, i.e. newest commits on top.
- Notice the label HEAD at the top, this indicates the commit that the current working directory is based on.


### What is the commit hash?
A commit hash is a string that uniquely identifies a specific commit. They are the really long list of numbers and letters that you can see in the output above after the word commit. For example, f50fddc8b03956ce453375c1cf5d5799e5ce7a51 for the last entry.
Occasionally, you will need to refer to a specific commit using the hash. Normally, you can use just the first 5 or 6 elements of the hash (eg. for the hash above it will be enough to use f50fdd) as it is very unlikely that there will be two commit hashes with identical starting elements.
Throughout this course, we will indicate that you need to use the hash with [commit-hash]. On those occasions, replace the whole string (including the square brackets!) with the hash id. For example, if you need to use git show (see example below) with the above commit hash, you will run:
```bash
git show f50fdd
```
**Output**

```bash
commit f50fddc8b03956ce453375c1cf5d5799e5ce7a51
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 12:25:09 2022 +0000

    write ingredients

diff --git a/food/pizza.txt b/food/pizza.txt
new file mode 100644
index 0000000..6da9b0a
--- /dev/null
+++ b/food/pizza.txt
@@ -0,0 +1,24 @@
+Pizza Margherita in 4 easy steps:
+(from bbc good food) 
+
+-----------Ingredients---------
+
+For the base
+
+300g strong bread flour
+1 tsp instant yeast (from a sachet or a tub)
+1 tsp salt
+1 tbsp olive oil, plus extra for drizzling
+For the tomato sauce
+
+100ml passata
+handful fresh basil or 1 tsp dried
+1 garlic clove, crushed
+For the topping
+
+125g ball mozzarella, sliced
+handful grated or shaved parmesan (or vegetarian alternative)
+handful of cherry tomatoes, halved
+
+
+handful of basil leaves (optional)
```

Press **q** : to exit the commit 

## How to use git log
Lets see how we can create a commit history (different versions of the file), observe the changes of the file and recall the changes for a commit.

From the previous example we will change the pizza.txt file. This time I'll change the tomato sauce.

```bash
nano pizza.txt
cat pizza.txt     ## view the text 
```
Make the commit:

```bash 

git add pizza.txt
git commit -m 'alter tomato sauce'
```

**Output**

```bash 
[main 66053c9] alter tomato sauce
 1 file changed, 6 insertions(+), 4 deletions(-)
```

With **git log** we see all the commits

```bash 
git log
```

**Output**

```bash 
commit 66053c9473353ade36455bb17f6f3e3edfd2d320 (HEAD -> main)
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 18:23:17 2022 +0000

    alter tomato sauce

commit cebdb2ced222527abc2b062c804487e9c179bc6c
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 12:32:43 2022 +0000

    first changes

commit f50fddc8b03956ce453375c1cf5d5799e5ce7a51
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 12:25:09 2022 +0000

    "write ingredients"
```
To avoid having git log cover your entire terminal screen, you can limit the number of commits that Git lists by using -N, where N is the number of commits that you want to view. For example, if you only want information from the last commit you can use:

```bash 
git log -1
```

**Output**

```bash 
commit 66053c9473353ade36455bb17f6f3e3edfd2d320 (HEAD -> main)
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 18:23:17 2022 +0000

    "alter tomato sauce"
```
Here it shows the last (-1 ) commit with its hash number, the author, time and the message.

 You can also reduce the quantity of information using the --oneline option and see only the commit hast and the message.
 **log --oneline** is a very useful command

 ```bash
 git log --oneline
 ```

 **Output**
 ```bash
66053c9 (HEAD -> main) alter tomato sauce
cebdb2c first changes
f50fddc write ingredients
```
## How to see the differences with git diff

Lets make more changes and watch them with **git diff**

```bash
 nano pizza.txt
cat pizza.txt
```
 **Output**
 ```bash
-----------Ingredients---------

For the base

300g strong bread flour
1 tsp instant yeast (from a sachet or a tub)
1 tsp salt
1 tbsp olive oil, plus extra for drizzling

For the tomato sauce
(I use only fresh ingredients and cook them)
150 gr fresh tomatos diced
1 garlic glove smashed
1/2 onion
2 tbs olive oil. 
fresh  basil 


For the topping
125g ball mozzarella, sliced
handful grated or shaved parmesan (or vegetarian alternative)
handful of cherry tomatoes, halved
handful of basil leaves (optional)
```

If you want to see the differences before staging the file use **git diff**

 ```bash
 git diff
```
 **Output**
 ```bash
 diff --git a/food/pizza.txt b/food/pizza.txt
index 81d710a..65dfc61 100644
--- a/food/pizza.txt
+++ b/food/pizza.txt
@@ -13,14 +13,14 @@ For the base
 For the tomato sauce
 (I use only fresh ingredients and cook them)
 150 gr fresh tomatos diced
+1 garlic glove smashed
+1/2 onion
 2 tbs olive oil. 
-handful fresh basil 
+fresh  basil 
 
 
 For the topping
 125g ball mozzarella, sliced
 handful grated or shaved parmesan (or vegetarian alternative)
 handful of cherry tomatoes, halved
-
-
 handful of basil leaves (optional)
 ```

If you observe there ate two lines which are added (+) and one that is removed (-).

Lets put the change in the staging are and see what **git diff** reports
```bash
git add pizza.txt
git diff
```

Now there is no output. 
as far as Git can tell, there’s no difference between what it’s been asked to save permanently and what’s currently in the directory. However, if we do this:

```bash

git diff --staged
```
**Output**
```bash
diff --git a/food/pizza.txt b/food/pizza.txt
index 81d710a..65dfc61 100644
--- a/food/pizza.txt
+++ b/food/pizza.txt
@@ -13,14 +13,14 @@ For the base
 For the tomato sauce
 (I use only fresh ingredients and cook them)
 150 gr fresh tomatos diced
+1 garlic glove smashed
+1/2 onion
 2 tbs olive oil. 
-handful fresh basil 
+fresh  basil 
 
 
 For the topping
 125g ball mozzarella, sliced
 handful grated or shaved parmesan (or vegetarian alternative)
 handful of cherry tomatoes, halved
-
-
 handful of basil leaves (optional)
```

It shows us the difference between the last committed change and what’s in the staging area.
ometimes, e.g. in the case of the text documents a line-wise diff is too coarse. That is where the --color-words option of git diff comes in very useful as it highlights the changed words using colors.


 Let’s save our changes at the repo:

```bash
 git commit -m "add sauce ingredients"
```
```bash
git log --oneline    
```

**Output**
```bash                      
fb834e8 (HEAD -> main) add sauce ingredients
66053c9 alter tomato sauce
cebdb2c first changes
f50fddc write ingredients
```
Here we have all the commit hashes and messages. The latest commit is on HEAD

Now I open the editor of pizza.txt and I remove the last paragraph (The topping )
```bash
nano pizza.txt
```

I have now changed what it was HEAD before. To check the changes 

```bash
 git commit -m "add sauce ingredients"
```
```bash
git diff HEAD pizza.txt  
```

**Output**
```bash                      
diff --git a/food/pizza.txt b/food/pizza.txt
index 65dfc61..e0c4a60 100644
--- a/food/pizza.txt
+++ b/food/pizza.txt
@@ -19,8 +19,4 @@ For the tomato sauce
 fresh  basil 
 
 
-For the topping
-125g ball mozzarella, sliced
-handful grated or shaved parmesan (or vegetarian alternative)
-handful of cherry tomatoes, halved
-handful of basil leaves (optional)
```
It shows that I have removed the last 5 lines

You will get the same output if you just run **git diff pizza.txt**

The real goodness in all this is when you can refer to previous commits. We do that by adding ~1 (where “~” is “tilde”, pronounced [til-duh]) to refer to the commit one before HEAD.


```bash
git diff HEAD~2 pizza.txt
```
**Output**
```bash
diff --git a/food/pizza.txt b/food/pizza.txt
index 6da9b0a..e0c4a60 100644
--- a/food/pizza.txt
+++ b/food/pizza.txt
@@ -9,16 +9,14 @@ For the base
 1 tsp instant yeast (from a sachet or a tub)
 1 tsp salt
 1 tbsp olive oil, plus extra for drizzling
-For the tomato sauce
 
-100ml passata
-handful fresh basil or 1 tsp dried
-1 garlic clove, crushed
-For the topping
+For the tomato sauce
+(I use only fresh ingredients and cook them)
+150 gr fresh tomatos diced
+1 garlic glove smashed
+1/2 onion
+2 tbs olive oil. 
+fresh  basil 
 
-125g ball mozzarella, sliced
-handful grated or shaved parmesan (or vegetarian alternative)
-handful of cherry tomatoes, halved
 
 
-handful of basil leaves (optional)
```
Here we see all the differences (+) or (-) 3 versions backwards.
Press Q to exit 

If you want to see the file teh changes as well as the commit you can use **git show HEAD~2**

```bash 
$ git show HEAD~2 pizza.txt

```

**Output**
```bash
commit 66053c9473353ade36455bb17f6f3e3edfd2d320
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 18:23:17 2022 +0000

    alter tomato sauce

diff --git a/food/pizza.txt b/food/pizza.txt
index 6da9b0a..81d710a 100644
--- a/food/pizza.txt
+++ b/food/pizza.txt
@@ -9,13 +9,15 @@ For the base
 1 tsp instant yeast (from a sachet or a tub)
 1 tsp salt
 1 tbsp olive oil, plus extra for drizzling
+
 For the tomato sauce
+(I use only fresh ingredients and cook them)
+150 gr fresh tomatos diced
+2 tbs olive oil. 
+handful fresh basil 
 
-100ml passata
-handful fresh basil or 1 tsp dried
-1 garlic clove, crushed
-For the topping
 
+For the topping
 125g ball mozzarella, sliced
:
```
Press Q after the semicolon

```bash
git log --oneline

Output
fb834e8 (HEAD -> main) add sauce ingredients
66053c9 alter tomato sauce
cebdb2c first changes
f50fddc write ingredients
```
if you want to see the file with commit hash 66053c9 use 
git checkout 66053c9 pizza.txt
Be careful to add the file at the end, otherwise you will be in "detached HEAD" state

```bash 
git checkout 66053c9 pizza.txt
cat pizza.txt # To see the file at that version
```
**Output**
```bash
Pizza Margherita in 4 easy steps:
(from bbc good food) 

-----------Ingredients---------

For the base

300g strong bread flour
1 tsp instant yeast (from a sachet or a tub)
1 tsp salt
1 tbsp olive oil, plus extra for drizzling

For the tomato sauce
(I use only fresh ingredients and cook them)
150 gr fresh tomatos diced
2 tbs olive oil. 
handful fresh basil 


For the topping
125g ball mozzarella, sliced
handful grated or shaved parmesan (or vegetarian alternative)
handful of cherry tomatoes, halved


handful of basil leaves (optional)
```

![git checkout](./fig/git_checkout.png)







## Key points

- **git diff Head~ 2** or 
  *git diff [ID] FILENAME** displays differences between commits.
  It's good to check the file before staging 
  At staging is git diff --stage
  To see the differences in various versions use **git diff HEAD ~3 filename** (see 3 versions   
  backwards. The same is with **git diff 50fddc8b03956ce453375c1cf5d5799e5ce7a51 filename**
- **git checkout 6053c9 filename.txt** recovers old versions of files.
  Beware to use the filename!!! 
