# 9 Machine Dependent Features

- The machine instruction sets are different on each machine where `as` runs.

- Some versions of `as` support special pseudo-instructions for branch optimization.

- This chapter discusses most of these differences, though it does not include details on any machine's instruction set.

## 9.4 ARM Dependent Features

### 9.4.1 Options

#### `-march=*architecture*[+extension...]`

- This option specifies the target architecture.

- The following architecture names are recognized: `armv7-m`.

### 9.4.2 Syntax

#### 9.4.2.1 Instruction Set Syntax

- Two slightly different syntaxes are support for ARM and THUMB instructions.

    - The default, `divided`, uses the old style where ARM and THUMB instructions had their own, separate syntaxes.

    - The new, `unified` syntax, which can be selected via the `.syntax` directive.

### 9.4.4 ARM Machine Directives

#### `.arch *name*`

- Select the target architecture.

- Valid values for *name* are the same as for the `-march` command-line option without the instruction set extension.

- Specifying `.arch` clears any previously selected architecture extensions.

#### `.code [16|32]`

- This directive selects the instruction set being generated.

- The value 16 selects Thumb, with the value 32 selecting ARM.

#### `.syntax [unified | divided]`

- This directive sets the Instruction Set Syntax as described in the Section 9.4.2.1.

#### `.thumb`

- This performs the same action as *`.code 16`*.

#### `.thumb_func`

- This directive specifies that the following symbol is the name of a Thumb encoded function.

- This information is necessary in order to allow the assembler and linker to generate correct code for interworking between Arm and Thumb instructions and should be used even if interworking is not going to be performed.

- The presence of this directive also implies `.thumb`.

- This directive is not necessary when generating EABI objects.

    - On these targets the encoding is implicit when generating Thumb code.
