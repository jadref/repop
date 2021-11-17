# repop
auto replicating operators in matlab

Replicating arithmetical and logical operators.

Does element by element operations on X and Y where non-same sized dimensions are implicity wrapped round to match the size of the larger
to give a result matrix Z with size max(size(X),size(Y));

In general this is at least 2x faster than the equivalent matlab code using repmats and has the advantage of requiring no additional memory.

Example Usage:
X = randn(10000,10); example signal with data in rows
stdX = repop(X,mean(X,1),'-'); subtract the mean vector
stdX = repop(stdX,std(stdX,0,1),'/'); % divide by std-deviation

Operator can be one of:

Arthemetical -- returns a double matrix
'+','.+',plus - Implicitly repmatted elementwise addition
'-','.-',minus - Implicitly repmatted elementwise addition
'*','.*',times - Implicitly repmatted elementwise multiplication
'^','.^',power - Implicitly repmatted elementwise raise X to power Y
'\','.\',ldivide- Implicitly repmatted elementwise divide Y by X
'/','./',rdivide- Implicitly repmatted elementwise divide X by Y

Relational -- returns a logical matrix
N.B. for complex inputs the <,>,<=,>= operators are based upon abs(x)
(not real(x) as in matlab)
'==',eq - Implicitly repmatted elementwise equality
'~=',ne - Implicitly repmatted elementwise dis-equality
'<' ,lt - Implicitly repmatted elementwise less than
'>' ,gt - Implicitly repmatted elementwise greater than
'<=',le - Implicitly repmatted elementwise less than equal
'>=',ge - Implicitly repmatted elementwise greater than equal
