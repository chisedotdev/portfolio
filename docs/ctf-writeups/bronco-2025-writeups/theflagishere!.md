# theflagishere!

> CATEGORY - REVERSING

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fa98vdMUVn8DOhYEYYhoS%2Fimage.png?alt=media&#x26;token=61bad844-759e-4748-a5df-72d93d1770f5" alt=""><figcaption></figcaption></figure>

## Introduction

In this reversing challenge, I was given a Python compiled `.pyc` file. The description hinted that the program was supposed to determine the flag, but it didn't explicitly display it. My task was to reverse-engineer the file and extract the correct flag.

## Steps

### Step 1: Decompiling the `.pyc`  file

Since a `.pyc` file is a compiled Python file, I needed to decompile it back to readable Python code. To do this, I used an online tool: [lddgo.net Python Decompiler](https://www.lddgo.net/en/string/pyc-compile-decompile). I uploaded the `.pyc` file, and it provided me with the following Python script:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F7Bs7GfSjVvAOI1cSK2OS%2Fimage.png?alt=media&#x26;token=3ae949c5-425a-4297-81eb-850b68f19f8b" alt=""><figcaption></figcaption></figure>

### Step 2: Identifying Issues in the Code

After analyzing the decompiled code, I noticed a few issues:

* The `what_do_i_do` function contained a `return` inside a loop that would never execute properly.
* There were several unnecessary function calls that seemed misleading.
* Some of the flag extraction logic seemed obfuscated but could be simplified

I corrected the function:

```python
def what_do_i_do(whoKnows):
    a_st = {}
    for a in whoKnows:
        if a not in a_st:
            a_st[a] = 1
        else:
            a_st[a] += 1

    variable_name = 0
    not_a_variable_name = None
    for a in a_st:
        if a_st[a] > variable_name:
            not_a_variable_name = a
            variable_name = a_st[a]

    return (not_a_variable_name, variable_name)
```

### Step 3: Extracting the Flag

After fixing the logic, I reconstructed the flag by calling the appropriate functions in sequence:

```python
# Construct the flag
flag = (
    char_0() + char_1_4_6() + char_2_5_9() + char_3() +
    char_1_4_6() + char_2_5_9() + char_1_4_6() + char_7() +
    char_8() + char_2_5_9() + char_10()
)

print("Extracted flag: bronco{" + flag + "}")
```

Running the script printed the final flag:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F9VRzJW91dkGXHCIrVrgH%2Fimage.png?alt=media&#x26;token=70cf2341-c803-477e-9fac-eb9dd5056cee" alt=""><figcaption></figcaption></figure>

```python
flag: bronco{i_am_a_flag}
```

That’s how I solved this challenge. Thanks for reading!
