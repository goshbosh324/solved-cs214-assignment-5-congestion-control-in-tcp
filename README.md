Download Link: https://assignmentchef.com/product/solved-cs214-assignment-5-congestion-control-in-tcp
<br>
<span class="kksr-muted">Rate this product</span>




The objective of this project is to emulate the TCP congestion control algorithm, as explained below.

1.1 Assumptions and Variables:

The assumptions and variables are given below:

• Receiver Window Size is set to 1 MB, and does not change during the entire duration of the emulation.

• The Sender always has data to send to the receiver.

• Sender’s MSS is 1 KB. Each segment has a fixed length of one MSS.

• Go-back-N is used, but cumulative acknowledgments are not considered. For each segment, an individual timeout timer and ACK are used.

• The congestion window is always intrepreted as a multiple of MSS (1 KB).• The congestion threshold is always set to 50% of the current CW value.• Ki, 1 ≤ Ki ≤ 4 denotes the initial congestion window (CW). Default value is 1. The initial CW is given by:

CWnew = Ki ∗ MSS• Km, 0.5 ≤ Km ≤ 2 denotes the multiplier of Congestion Window, during exponential growth phase.

Default value is 1. When a segment’s ACK is successfully received, CWnew = min(CWold + Km ∗ MSS, RWS)

• Kn, 0.5 ≤ Kn ≤ 2 denotes the multiplier of Congestion Window, during linear growth phase. Default value is 1. When a segment’s ACK is successfully received,

CWnew = min(CWold + Kn ∗ MSS ∗ MSS/CWold, RWS)

 Kf , 0.1 ≤ Kf ≤ 0.5 denotes the multiplier when a timeout occurs:

CWnew = max(1, Kf ∗ CWold)• Ps, 0 &lt; Ps &lt; 1, denotes the probability of receiving the ACK packet for a given segment before its

timeout occurs.

1.2 Running the program

The program is invoked with the following command-line parameters:% ./cw -i &lt;double&gt; -m &lt;double&gt; -n &lt;double&gt; -f &lt;double&gt; -s &lt;double&gt; -T &lt;int&gt; -o outfile

The values correspond to Ki, Km, Kn, Kf , Ps and the total number of segments to be sent before the emulation stops. The output (specified below) is saved in an output file.

The congestion window progression is done on a slot-by-slot basis. In each “round” as explained in the class, a set of segments are sent, in proportion to the current value of CW, i.e. N = ceiling (CW/MSS). For example, if CW is equal to 4.3 KB, five packets are sent. However, the CW growth is based on MSS values as explained earlier. For each segment transmitted, the ACK for this segment is received before timeout with random probability Ps, and timeout occurs with probability (1 − Ps). Depending on this outcome, the CW increases and decreases as described earlier.

2 What to do?

Given the set of input parameters, the simulation progresses as above. The congestion window value is printed to the output file (one per line) at each CW update. A graph with x-axis being the update number and y-axis the corresponding CW value must be plotted.

A technical report must be written based on the results and graphs obtained for the following parameter combinations:

Ki ∈ {1, 4}; Km ∈ {1, 1.5}; Kn ∈ {0.5, 1}; Kf ∈ {0.1, 0.3}; Ps ∈ {0.01, 0.0001}.The report should explain how these factors influence the CW change over the duration of the session.

3 What to Submit?

The platform for this project will be Linux and C. Create a tar-gz file with name: &lt;RollNo&gt;-Lab5.tgz The directory should contain the following files:

• Source File(s), Please prefix your files with RollNumbers

&lt;ROLLNUM&gt;_Sender.c, &lt;ROLLNUM&gt;_Receiver.c• A Script file obtained by running UNIX command script which will record the way you have

finally tested your program.• Technical Report (as above)

• a README file containing instructions to compile, run and test your program.

• Please copy your output and paste it to related program at the end of source code(please comment it)/ if necessary you can take screen shot name it with its question number and put it in a same folder.

Test well before submission. Follow some coding style uniformly. Provide proper comments in your code.

After completing all the tasks please show it to TA’s. Once the result is correct then only we allow you to upload to the moodle.

Submit only through moodle and well in advance. Any hiccups in the moodle/Internet at the last minute is never acceptable as an excuse for late submission. Submissions through email will be ignored.

4 Help

1. Ask questions EARLY and start your work NOW (really, no choice). Take advantage of the help of the Tas and the instructor.

2. Submissions PAST the extended deadline SHOULD NOT be mailed to the TAs. Only submissions approved by the instructor or uploaded to Moodle within the deadline will be graded.

3. Demonstration of code execution to the TAs MUST be done using the student’s code uploaded on Moodle.

4. NO sharing of code between students, submission of downloaded code (from the Internet, Campus LAN, or anywhere else) is allowed. The first instance of code copying will result in ZERO marks for the Lab component of the Course Grade. The second instance of code copying will result in a ’FR’ Course Grade. Students may also be reported to the Campus Disciplinary Committee, which can impose additional penalties.