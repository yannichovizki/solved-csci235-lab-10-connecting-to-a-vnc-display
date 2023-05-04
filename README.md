Download Link: https://assignmentchef.com/product/solved-csci235-lab-10-connecting-to-a-vnc-display
<br>
You will use a lab account for a VNC display. The lab account already started a VNC session, so you don’t need to do Step 3 or 4 of Lab 7’s Task #1. Two steps that you need to do are:

<ol>

 <li>Create a tunnel from your machine to a VNC display (Step 5 of Lab 7’s Task #1).

  <ol>

   <li>A cslab machine number and a display number will be provided to you.</li>

   <li>For example, if the given machine is <strong>cslab10</strong>, and the display number is <strong>12</strong>, the command for creating a tunnel to the display will be:

    <ul>

     <li>Mac Terminal: ssh –L 5901:localhost:<strong>5912</strong> <em>your_loginID</em>@<strong>cslab10</strong>.wheaton.edu</li>

     <li>Windows PuTTY:</li>

    </ul></li>

  </ol></li>

</ol>

Host Name: <strong>cslab10</strong>.wheaton.edu

For Connection, SSH, Tunnels: 5901 for the “Source port” and localhost:<strong>5912</strong> for the “Destination”.

<ol>

 <li>The CS system will prompt for your (ID and) password as usual.</li>

</ol>




<ol start="2">

 <li>Start a VNC viewer on your machine (Step 6 of Lab 7’s Task #1).

  <ol>

   <li>The given display’s VNC password will be provided. You need to use this password to connect to the display.</li>

  </ol></li>

</ol>




Tips:

<ul>

 <li>If you don’t see the menu bar at the top of the CS desktop window, right-click the desktop screen to get Applications menu.</li>

 <li>When you are done with the desktop, close the desktop and connection by doing:

  <ul>

   <li>For TightVNC, use the X button at the top corner of the window.</li>

   <li>For Mac, in Screen Sharing menu at the top, select Connection, and select Close.</li>

  </ul></li>

</ul>




===

<h1>Recursive methods for tree traversals Parse trees</h1>

<strong> </strong>

<strong>Documentation and styling of your code will be part of your grade.</strong>




Create a new directory and cd to it. Then copy starting files from the course directory to your current directory.

$ cp /cslab/class/csci235/labs/lab10/* .

You should have four Java files and one class file (ExprStringSlicer.class) in the directory.







<h1>Task #1: Writing recursive TreeNode methods</h1>

TreeNode is a class for a binary tree, and TreeDriver tests the TreeNode class.




Open the two files, and inspect the code. Draw a diagram for the tree that will be built by the driver. Compile and run the driver.

Switch to TreeNode.java, and inspect the instance variables and its methods. Trees are naturally traversed in a recursive manner, and thus you will write recursive methods for TreeNode. Analyze the code of count(). It returns the number of nodes in the subtree rooted at the node on which it is called. Note that the number of nodes is 1 (for the current node, the calling object) plus the number of nodes in its left subtree, plus the number of nodes in its right subtree.

<ul>

 <li>It is a recursive method, but no explicit base case has been coded. What base case has been implied in the code? What value will be returned when the base case is executed?</li>

</ul>




Recall the <em>preorder</em>, <em>inorder</em>, and <em>postorder</em> traversals shown in class. Write the three, recursive display methods. Refer to the code of count()for different cases on a node. Update the System.out.println() statements in TreeNode so that the integers at the nodes are <strong><u>printed on a single line</u></strong>.

<strong> </strong>

Test your recursive methods with the original driver. You may need to edit the original code.

Test the methods again with several, new trees: trees with nodes that have only a left child or only a right child.




<h1>Task #2: Parse trees</h1>

For this task, you will use the three files: ExprNode.java, ExprStringSlicer.class, and Interpreter.java.

Interpreter is the driver, and ExprNode is the interface that we discussed in class. The main method of the driver calls parse, and its first line is as follows:




String nodes[] = ExprStringSlicer.slice(expr);




What would be the heading of the slice method? Is this a static method, or an instance method? The source code of ExprStringSlicer is not given, but you can still use the program because its class file is provided.




ExprStringSlicer.slice() is the method to get a string array for building an expression tree. This method works as follows:

<ul>

 <li>It takes a string of either an integer or (<em>expression op expression</em>) as seen in class.</li>

 <li>It returns an array of strings. o If the input string contains just an integer, the string will be referred by the first element of the string array. The array size will be 1.

  <ul>

   <li>If the input string consists of <em>expression</em>, <em>op</em>, and <em>expression</em>, the first expression will be referred by the first element, the <em>op</em> will be referred by the second element, and the second expression will be referred by the third element of the array. The array size will be 3.</li>

  </ul></li>

</ul>




For example, when expr is “(42-17)”, nodes[0] refers to “42”; nodes[1] refers to “-“; and nodes[2] refers to “17”.

<ul>

 <li>If expr is “10”, nodes[0] refers to “10”.</li>

 <li>If expr is “((18*10)/18)”, nodes[0] refers to “(18*10)”; nodes[1] refers to “/”; and nodes[2] refers to “18”.</li>

</ul>




<u>Step #1</u>: Write two classes that implement the ExprNode interface: one for ConstantNode and the other for OperatorNode. No starting file is provided for these classes. Refer to the example code in Exercises #7. Compile the two Java files.




<u>Step #2</u>: Complete the parse() method in Interpreter. The main method is complete.

<ul>

 <li>Read the block comment carefully. The returning ExprNode will be the root of the expression tree. o What expression? Where will it be returned? What is the variable that holds this returned value?

  <ul>

   <li>In the main, what does the statement, evaluate() do?</li>

  </ul></li>

 <li>See the condition of the base case.

  <ul>

   <li>Why does it become the base case? o What should be assigned to out?</li>

  </ul></li>

 <li>Complete the recursive case. o What will be assigned to nodes[]? How to use the array’s string objects to build the tree?

  <ul>

   <li>What should be assigned to out?</li>

  </ul></li>

</ul>




Hand-test your code for parse() by drawing a diagram for the input “((2*5)/3)”. If your code builds a proper tree for the input, run Interpreter.java with the input. The output should be 3. Test your program with several, different expressions.





