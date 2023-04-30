Download Link: https://assignmentchef.com/product/solved-cs235-project-5-find-route-in-map
<br>
For this project you will <strong>design</strong> and <strong>implement </strong>two classes (City and RouteMap) to find a route, if one exists, from origin to destination city, given a particular map.

This project will build on ideas we have worked with already (reading input from a file, working with abstractions – i.e. a City and a RouteMap).

However this time you will be responsible for the design!

<strong>GitHub Classroom assignment link: </strong><strong>https://classroom.github.com/a/BatrQod8</strong>

<strong>The idea: </strong>In a map, as the one pictured above, we say that R is <strong><em>reachable</em></strong> from P because there is an arrow going from P to R (<em>you can go from P to R)</em>. However, P is NOT reachable from R because you cannot go from R to P following a single arrow. A <strong><em>route</em></strong> from an origin city to a destination city is a sequence of cities s.t. each city in the sequence is reachable from the previous one. As we discussed in lecture, it is possible to find out if there is a route from an origin city to a destination city  by implementing <strong>backtracking using a stack</strong>

<ul>

 <li>Starting from the origin, push reachable cities <u>that have not yet been visited</u> onto the stack, and mark them as having been visited.</li>

 <li>If you reach a dead end (no more unvisited reachable cities available from the city at the top of the stack), <strong>pop the stack to backtrack. </strong></li>

 <li>Stop when you either <strong>have the destination at the top of the stack</strong> (<strong>found route!)</strong> or the <u>stack is empty</u> (<u>there is no route</u>)</li>

</ul>

<strong>The input: </strong>The input will be in the following format:

<ul>

 <li>The first line will be a comma-separated list of city names in alphabetical order. For example, for the RouteMap pictured above, <strong>the first line </strong>in the corresponding input file will be:</li>

</ul>

<h1>P,Q,R,S,T,W,X,Y,Z
</h1>

<ul>

 <li>The remainder of the file will be a comma separated list of city pairs separated by ‘-‘, where the second city in the pair is reachable from the first. For example, for the RouteMap pictured above, the remainder of the file will be:</li>

</ul>

<h1>P-R,P-W,Q-X,R-X,S-T,T-W,W-Y,W-S,Y-R,Y-Z
</h1>

<u>You may assume </u>that the city names are unique (no two cities have the same name) but not necessarily single letters, and that the input file is in the correct format.

<strong>Design and Implementation: </strong>

You will <strong>design</strong> and <strong>implement</strong> the two classes: City (City.hpp and City.cpp) and RouteMap (RouteMap.hpp and RouteMap.cpp) <strong> </strong>

<strong> </strong>

<strong><u>Design Requirements</u> – </strong>to successfully implement backtracking using a stack you need to:

<ul>

 <li>Be able to mark a city as having been visited</li>

 <li>Find out what cities are reachable from any given city</li>

</ul>

<h1><strong>Furthermore</strong></h1>

<ul>

 <li>The <strong>RouteMap </strong>class <strong>must have</strong> the following <strong>3</strong> <strong>public</strong> <strong>methods</strong> (you may and <u>should</u> add any public and private members that you deem necessary to implement and support the following)</li>

</ul>

/**

<strong>@param</strong> input_file_name of a csv file representing a route map where the first       line is a comma-separated list of city names, and the remainder is a        comma-separated list of city-pairs of the form A-B, indicating that B         is reachable from A

(i.e. there is an arrow in the map going from A to B)

<strong>@post</strong> this depends on your design, the input data representing the map must       have been stored. <strong>Reachable cities must be stored and explored in the           same order in which they are read from the input file </strong>

**/

<strong>bool</strong><strong> readMap(</strong><strong>std</strong><strong>::</strong><strong>string</strong><strong> input_file_name);</strong>




/**

<strong>@return</strong> a pointer to the city found at position, where          0 &lt;= position &lt;= n-1, and n is the number of cities,
 
and cities are stored in the same order in which they appear          in the input file. Returns nullptr if city not found at position.

**/

<strong>const</strong> <strong>City</strong><strong>* </strong><strong>getCity</strong><strong>(</strong><strong>size_t</strong> <strong>position</strong><strong>); </strong>




/**

<strong>@return</strong> true if there is a route from origin to destination, false otherwise <strong>@post</strong> if a route is found from origin to destination, it will print it to        standard output in the form “ORIGIN -&gt; … -&gt; DESTINATION
”

**/

<strong>bool</strong> <strong>isRoute</strong><strong>(</strong><strong>City</strong><strong>* </strong><strong>origin</strong><strong>, </strong><strong>City</strong><strong>* </strong><strong>destination</strong><strong>); </strong>

For example, with the map in the above example,  isRoute(T_ptr, Z_ptr);  will return <strong>true</strong> and print

<h2>T -&gt; W -&gt; Y -&gt; Z</h2>

<strong>Project Notes: </strong>For this project I suggest that you use the STL stack for backtracking (#include &lt;stack&gt;)  as well as STL vectors or any other container you may deem appropriate to represent and store your data.

<a href="https://en.cppreference.com/w/cpp/container/stack">https://en.cppreference.com/w/cpp/container/stack</a>

<strong>Extra Credit: </strong>Add exception handling for reading an empty file and calling getCity with position greater than the number of cities. When catching the exception your program should output “Catching” (for grading purposes output to cout). In such cases, a call to isRoute should still return <strong>false.  </strong><strong>To receive extra credit you must implement this as a try/catch block, otherwise no extra credit will be awarded.</strong>

<strong>Testing: </strong>You should design and test incrementally. Write a main function to test your City class. Instantiate City objects and test every member function.

Next implement and test your RouteMap class, also incrementally. <u>You should</u> <u>produce different input files and test </u>that your RouteMap methods are correct on different test cases (there is a route, there is no route, there is a cycle, etc.)