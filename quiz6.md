# Quiz 6 Answers

### Q2: 

(Assuming blocks A-E map to set 0)

<table>
<thead>
<tr>

<th align="center">Referred Block</th>
<th>Cache vs Test Cache</th>
<th align="left">Hit/Miss Type</th>
</tr>
</thead>
<tbody>
<tr><td rowspan="2" align="center">A</td>
<td align="center"><table><tbody><tr><td>0</td><td>A</td><td>-</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Compulsory (first reference)</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>A</td><td>-</td><td>-</td><td>-</td></tr></tbody></table></td>
<td>Compulsory (first reference)</td>
</tr>

<tr><td rowspan="2" align="center">B</td>
<td align="center"><table><tbody><tr><td>0</td><td>A (lru)</td><td>B</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Compulsory (first reference)</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>A (lru)</td><td>B</td><td>-</td><td>-</td></tr></tbody></table></td>
<td>Compulsory (first reference)</td>
</tr>

<tr><td rowspan="2" align="center">A</td>
<td align="center"><table><tbody><tr><td>0</td><td>A </td><td>B (lru)</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Hit</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>A</td><td>B (lru)</td><td>-</td><td>-</td></tr></tbody></table></td>
<td>Hit</td>
</tr>

<tr><td rowspan="2" align="center">C</td>
<td align="center"><table><tbody><tr><td>0</td><td>A (lru)</td><td>C</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Compulsory (first reference)</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>A</td><td>B (lru)</td><td>C</td><td>-</td></tr></tbody></table></td>
<td>Compulsory (first reference)</td>
</tr>

<tr><td rowspan="2" align="center">D</td>
<td align="center"><table><tbody><tr><td>0</td><td>D</td><td>C (lru)</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Compulsory (first reference)</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>A</td><td>B (lru)</td><td>C</td><td>D</td></tr></tbody></table></td>
<td>Compulsory (first reference)</td>
</tr>

<tr><td rowspan="2" align="center">E</td>
<td align="center"><table><tbody><tr><td>0</td><td>D (lru)</td><td>E</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Compulsory (first reference)</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>A (lru)</td><td>E</td><td>C</td><td>D</td></tr></tbody></table></td>
<td>Compulsory (first reference)</td>
</tr>

<tr><td rowspan="2" align="center">C</td>
<td align="center"><table><tbody><tr><td>0</td><td>C</td><td>E (lru)</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Conflict (set capacity)</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>A (lru)</td><td>E</td><td>C</td><td>D</td></tr></tbody></table></td>
<td>Hit</td>
</tr>

<tr><td rowspan="2" align="center">D</td>
<td align="center"><table><tbody><tr><td>0</td><td>C (lru)</td><td>D</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Conflict (set capacity)</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>A (lru)</td><td>E</td><td>C</td><td>D</td></tr></tbody></table></td>
<td>Hit</td>
</tr>

<tr><td rowspan="2" align="center">B</td>
<td align="center"><table><tbody><tr><td>0</td><td>B</td><td>D (lru)</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Capacity (cache cap)</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>B</td><td>E (lru)</td><td>C</td><td>D</td></tr></tbody></table></td>
<td>Capacity</td>
</tr>

<tr><td rowspan="2" align="center">E</td>
<td align="center"><table><tbody><tr><td>0</td><td>B (lru)</td><td>E</td></tr><tr><td>1</td><td>-</td><td>-</td></tr></tbody></table></td>
<td><b>Conflict (set capacity)</b></td>
</tr>
<tr>
<td align="center"><table><tbody><tr><td>B</td><td>E</td><td>C (lru)</td><td>D</td></tr></tbody></table></td>
<td>Hit</td>
</tr>
</tbody>
</table>

---------

### Q3:

Block size = 16 B, Assoc. = 2   
Number of block offset bits = $\log_2(16) = 4$   
With the last nibble removed:   
- Index + tag for block addr. `0x10004B70` = `0b... 0111`   
- Index + tag for block addr. `0x200055F4` = `0b... 1111`   
- Index + tag for block addr. `0x100092F2` = `0b... 1111`

$\therefore$ Minimum of __4__ index bits are required to assign blocks to different sets (with 2 blocks per set).

$\text{Number of sets} = \displaystyle \frac{\text{Cache Size}}{\text{Assoc.} \times \text{Block Size}}$    

$\text{Number of sets} =\displaystyle 2 ^ \text{index bits} = 16 $  
$\therefore \text{Cache size} = 16 \times 2 \times 16 = \mathbf{512} \textbf{B}$

---
### Q4:
 - **Graph 1** - Fixed Block size  
	Higher assoc. leads to lower miss rate.  
	Higher cache size eliminates non-compulsory misses.
	
 - **Graph 2** - Fixed Cache & Block size  
	Fixed cache size implies compulsory and capacity misses 
	cannot be eliminated.
	
 - **Graph 3** - Parabolic curve  
	Keeping cache size and assoc. fixed, increasing block size 
	decreases miss rate up to a point. But larger blocks mean fewer
	blocks in cache, which increases miss rate after spatial locality
	is fully exploited.

---
### Q5:

1. Software prefetch distance   
	$k =\displaystyle \frac{\text{Miss Penalty}}{\text{Iteration Time}} =\displaystyle \frac{100}{25} = \mathbf{4}$
	
2. Since 4 elements of `a` fit in 1 block, when prefetching `a[i+4]`,    
	if $\texttt{i} \bmod 4$ = 0, 4 consecutive elements (`i+4..7`) of `a` are prefetched.   
	If $\texttt{i} \bmod 4$ = 1 or 2 or 3, prefetch hits (`i+5..7`)   
	$\therefore$ __3 out of 4 prefetch instructions are redundant__
	
3. 3 distinct arrays referenced   
	$\therefore$ __3 stream buffers can eliminate demand misses__
