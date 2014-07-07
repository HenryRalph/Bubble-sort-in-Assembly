Bubble-sort-in-Assembly
=======================
# Bubble sort by OBINNA OZOALOR
# r3 is used as the array pointer


	.data

list: 	.word 7, 8, 100, 50, 78, 90, -9, -3, 8, 13	# Array to be sorted
	.word 10, 91, 69, 78, 59, -2, -8, 7, 1, 98
	.word 88, 41, 73, 82, -1, 0, 7, 1, 3, 4
	.word 77, 50, 21, 12, 4, -6, 88, 9, 51, 6
	.word 101, 59, 31, 27, 23, 42, 41, 44, 9, 5 
n:	.word 50	

	.text
bubble: 
	ld	r2, n(r0)	# r2=n=10
	daddi	r4, r0, 1	# r4=pass=1	
do:
	daddi	r5, r0, 1	# r5=sorted=1
	daddi	r1, r0, 0	# r1=i=0
	daddi	r3, r0, 0
	dsub	r8, r2, r4	# r8=n-pass
for:
	slt	r9, r1, r8	# r9=1 if i<n-pass
	beqz	r9, NextPass
	ld	r6, 0(r3)	# r6=list[i]
	ld	r7, 8(r3)	# r7=list[i+1]	
	slt	r10, r7, r6	# r10=1 if list[i+1]<list[i]
	beqz	r10, NoSwap
	sd	r6, 8(r3)	# swap
	sd	r7, 0(r3)	# swap
	daddi	r5, r0, 0	# r5=sorted=0
NoSwap:
	daddi	r1, r1, 1	# i++
	daddi	r3, r3, 8	
	j	for
NextPass:
	daddi	r4, r4, 1
	daddi	r3, r3, 0
	beqz	r5, do

	halt 
