####TEST


M=M+1

@R1

D=M

@R3

D=M-D

@NO_RIGHT

D;JLT 

@R1

M=M-1

@R1

A=M

M=-1 

@R1

D=M

@R2

M=D    

@LOOP

0;JMP

@R2

M=0  

@R1

M=M-1 

@R1

D=M

@R4

D=M-D

@NO_LEFT

D;JLT 

@R1

M=M+1  

@R1

A=M

M=-1  

@R1

D=M

@R2

M=D  

@LOOP

0;JMP



https://github.com/user-attachments/assets/8a693765-a17d-4376-9a89-a697ba4e79d0


