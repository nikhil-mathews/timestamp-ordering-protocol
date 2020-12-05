# timestamp-ordering-protocol
timestamp ordering protocol based on DATABASE SYSTEM CONCEPTS Seventh Edition Abraham Silberschatz Yale University Henry F. Korth Lehigh University S. Sudarshan Indian Institute of Technology, Bombay
Thomas right rule is used.

Run from terminal
sample input: st1; st2; w1(A); r2(B); w1(B)

Suppose a transaction Ti issues a read(Q)
1. If TS(Ti) ≤ W-timestamp(Q), then Ti needs to read a value of Q that
was already overwritten.
▪ Hence, the read operation is rejected, and Ti is rolled back.
2. If TS(Ti) ≥ W-timestamp(Q), then the read operation is executed, and
R-timestamp(Q) is set to
max(R-timestamp(Q), TS(Ti)).

Suppose that transaction Ti issues write(Q).
1. If TS(Ti) < R-timestamp(Q), then the value of Q that Ti is producing
was needed previously, and the system assumed that that value
would never be produced.
➢Hence, the write operation is rejected, and Ti is rolled back.
2. If TS(Ti) < W-timestamp(Q), then Ti is attempting to write an
obsolete value of Q.
➢Hence, this write operation is rejected, and Ti is rolled back.
3. Otherwise, the write operation is executed, and W-timestamp(Q) is
set to TS(Ti).

Thomas right rule:
When Ti attempts to write data item Q, if TS(Ti) < W-timestamp(Q), then Ti is
attempting to write an obsolete value of {Q}.
• Rather than rolling back Ti as the timestamp ordering protocol would
have done, this {write} operation can be ignored.
