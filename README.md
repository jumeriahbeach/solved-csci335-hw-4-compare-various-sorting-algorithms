Download Link: https://assignmentchef.com/product/solved-csci335-hw-4-compare-various-sorting-algorithms
<br>



<strong>Learning Outcome:   The goal of this assignment is to use and compare various sorting algorithms. </strong>

In this assignment you are going to compare various sorting algorithms. You will also modify the algorithms in order for a Comparator class to be used for comparisons. You will then further experiment with algorithmic variations.

<strong>Code Files provided: </strong>

<ol>

 <li>h (Chapter 7)</li>

 <li>cc</li>

</ol>

You should write a small function that verifies that a collection is in sorted order.

<strong>template&lt;typename Comparable, typename Comparator&gt; bool VerifyOrder(const vector&lt;Comparable&gt; &amp;input, Comparator less_than) </strong>

The above function should return true if and only if the input is in sorted order according to the Comparator. For example, in order to check whether a vector of integers (vector&lt;int&gt; input_vector) is sorted from smaller to larger, you need to call:

<strong>VerifyOrder(input_vector, less&lt;int&gt;{});  </strong>

If you want to check whether the vector is sorted from larger to smaller you need to call

<strong>VerifyOrder(input_vector, greater&lt;int&gt;{});  </strong>

This function should be placed inside test_sorting_algorithms.cc

<strong><u>All deliverables are described at the end of the file.</u></strong><strong>  </strong>

Next, you should write two functions, one that generates a random vector, and another that generates a sorted vector. The sorted vector should generate a vector of increasing or decreasing values based on bool smaller_to_larger.  You will use both of these for your own testing purposes.

The function signatures should be as follows

1) vector&lt;int&gt; GenerateRandomVector(size_t size_of_vector) 2) vector&lt;int&gt; GenerateSortedVector(size_t size_of_vector, bool smaller_to_larger)




Next, write a function that computes the duration given a start time and stop time in nanoseconds. Hint: Look at the TestTiming function given to you in test_sorting_algorithms.cc:

The function signature should be as follows.

auto ComputeDuration(chrono::high_resolution_clock::time_point start_time, chrono::high_resolution_clock::time_point end_time)

<strong><u>These functions should be placed inside</u></strong><strong><u> test_sorting_algorithms.cc</u></strong><strong> <u>All deliverables are described at the end of this document.</u></strong>




You will now modify several sorting algorithms provided to you in Sort.h.  You will modify:

<strong>Heapsort, Quicksort, and Mergesort. </strong>

<table width="0">

 <tbody>

  <tr>

   <td colspan="2" width="523"><strong>You should modify these algorithms so that they each take a Comparator with their </strong></td>

  </tr>

  <tr>

   <td width="37"><strong>input.</strong></td>

   <td width="485"><strong> </strong></td>

  </tr>

 </tbody>

</table>

The signatures for these sorts should be:

<strong>template &lt;typename Comparable, typename Comparator&gt; void HeapSort(vector&lt;Comparable&gt; &amp;a, Comparator less_than) </strong>

<strong> template &lt;typename Comparable, typename Comparator&gt; void QuickSort(vector&lt;Comparable&gt; &amp;a, Comparator less_than) </strong>

<strong>  template &lt;typename Comparable, typename Comparator&gt; void MergeSort(vector&lt;Comparable&gt; &amp;a, Comparator less_than)   </strong>

<table width="0">

 <tbody>

  <tr>

   <td colspan="2" width="494">You <strong>will</strong> have to modify multiple functions, helpers and wrappers to make this fully</td>

  </tr>

  <tr>

   <td width="150">operational without error.</td>

   <td width="343"><strong> </strong></td>

  </tr>

 </tbody>

</table>

<h2>These functions should be modified and kept inside Sort.h</h2>

<strong><u>All deliverables are described at the end of this document.</u></strong>

<strong>Now that those two steps are finished, you will move on to testing. </strong>

You should now create a driver program, within <strong>test_sorting_algorithms.cc</strong>, that will test each of your modified sorts with different inputs.

The program will be executed as follows:

<strong>./test_sorting_algorithms &lt;input_type&gt; &lt;input_size&gt; &lt;comparison_type&gt;  </strong>

where <strong>&lt;input_type&gt;</strong> can be <strong>random</strong>,<strong> sorted_small_to_large</strong>, or<strong> sorted_large_to_small</strong>, <strong>&lt;input_size&gt;</strong> is the number of elements of the input, and <strong>&lt;comparison_type&gt;</strong> is either less or greater.




For example, you should be able to run

<strong>./test_sorting_algorithms random 20000 less  </strong>

The above should produce a random vector of 20000 integers, and apply all three algorithms using the <strong>less&lt;int&gt;{}</strong> Comparator.

You can also run:

<strong>./test_sorting_algorithms sorted 10000 greater  </strong>

The above will produce the vector of integers containing 1 through 10000 in that order, and will test the three algorithms using the <strong>greater&lt;int&gt;{}</strong> Comparator.

This driver should be implemented inside the <strong>sortTestingWrapper()</strong> function.  <strong>The formatting for driver output is shown at the bottom of the file. </strong>

<strong>Note: </strong><em>The format presented is an example for how you should test your functions. It serves as a good base of understanding of how the different sorts will vary in runtime, with different types of inputs. You will not be constrained (or graded exactly on how) you implement this step, but doing so would help you and us verify the accuracy of your work. <strong>(You still must create a driver that functions like the one described, but it will not be autograded for formatting, it will be manually looked at.)</strong></em><strong> <u>Q2 (20 points)</u>  </strong>

In this question, you will implement variations of the quicksort algorithm. You will investigate the following pivot selection procedures.

<ol>

 <li>a) Median of three (<strong>already implemented in part 2)</strong></li>

 <li>b) Middle pivot (always select the middle item in the array)</li>

 <li>c) First pivot (always select the first item in the array)</li>

</ol>

Although median of three is already implemented in the file, you will use it for comparisons further in this question.

The following two quicksort implementations, <strong>middle pivot</strong>, and <strong>first pivot</strong>, should have wrappers with the following signatures, that then call the full implementations.

<strong>//Middle Pivot Wrapper </strong>

<strong>template &lt;typename Comparable, typename Comparator&gt; void QuickSort2(vector&lt;Comparable&gt; &amp;a, Comparator less_than) </strong>

<strong> </strong>

<strong>//First Pivot Wrapper </strong>

<strong>template &lt;typename Comparable, typename Comparator&gt; void QuickSort3(vector&lt;Comparable&gt; &amp;a, Comparator less_than)</strong>

<strong><u>Note:</u></strong> <em>these are just the wrappers, you have to write the actual quicksort functionality in another function called by these (similar as in the original quicksort provided).</em>

<strong>In order to test these functions, you will add to the output of the driver described in Step 3. The full format is shown below deliverables. </strong>




Deliverables: You should submit these files:




<ul>

 <li>README file</li>

</ul>




<ul>

 <li>h (modified)

  <ul>

   <li>All sort modifications and additions should be kept within this file.</li>

  </ul></li>

 <li>cc (modified)

  <ul>

   <li>VerifyOrder() ○ GenerateRandomVector()</li>

  </ul></li>

</ul>

○ GenerateSortedVector()

○ ComputeDuration()

○ sortTestingWrapper()

<strong>Note: </strong>A large amount of this assignment will be manually checked and graded. We will run your sorts and implemented functions in the autograder, but the sort modifications will be verified manually.

<strong><u>Driver Formatting</u></strong>

<h2><em>The full driver format should be as follows: (example shown with function call </em></h2>

<strong>./test_sorting_algorithms random 20000 less</strong><strong><em>) </em></strong><em>Note: </em>The number output next to “Verified” is the boolean output of the function VerifyOrder(). If that value is 0, your sort did not work as intended.

Running sorting algorithms: random 20000 less

Heapsort

Runtime: &lt;X&gt; ns Verified: 1

MergeSort

Runtime: &lt;X&gt; ns Verified: 1

QuickSort

Runtime: &lt;X&gt; ns

Verified: 1

Testing Quicksort Pivot Implementations

Median of Three

Runtime: &lt;X&gt; ns

Verified: 1




Middle




Runtime: &lt;X&gt; ns

Verified: 1




First




Runtime: &lt;X&gt; ns

Verified: 1


