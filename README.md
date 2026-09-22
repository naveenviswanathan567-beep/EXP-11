--# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required

Anaconda - Python 3.7

## Algorithm:
#### Step1:

- Read the input string.

- Count the number of occurrences of each character.

- Store each character and its frequency in a dictionary.

#### Step2:
- Create a node for each character. 

- Each node contains:
   - Character
   - Frequency

- Store all nodes in a list.

#### Step3:
- Sort the nodes based on frequency.

- Select the two nodes with the smallest frequencies.

- Combine them into a new node whose frequency is the sum of the two.

- Repeat until only one node remains.

- The remaining node is the Huffman tree/root.

#### Step4:
- Traverse the Huffman tree recursively.

- Assign 0 to the left branch.

- Assign 1 to the right branch.

- The sequence of 0s and 1s obtained at each leaf is the character's Huffman code.

#### Step5:
- Store the generated codes in a dictionary.

- Print each character along with its corresponding Huffman code.

## Program:

#### Developed by:
#### Name : NAVEEN 
#### Reg No : 212225240098

### Get the input String
```
#Step 1: Get the input string
input_string = "Kalpesh C"  # Example input string
```
### Calculate frequency of each character in the input string
```
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1
```
### Create tree nodes
```
nodes = [[char, freq] for char, freq in frequency.items()]
```
### Main function to implement huffman coding
```
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

#The final node is the Huffman tree
huffman_tree = nodes[0]
```
### Calculate frequency of occurrence
```
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):  # If it's a leaf node
        huffman_codes[tree[0]] = code
    else:  # If it's an internal node, recurse
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

```
### Print the characters and its huffmancode
```
print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")

```
## Output:
Print the characters and its huffmancode

![alt text](image.png)

## Result
Thus the huffman coding was implemented to compress the data using python programming.
