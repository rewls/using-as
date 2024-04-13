# 7. Assembler Directives

- The names are case insensitive for most targets, and usually written in lower case.

- This chapter discusses directives that are available regardless of the target machine configuration for the GNU assembler.

    - Some machine configurations provide additional directives.

    - See Chapter 9.

## 7.102 `.type`

- This directive is used to set the type of a symbol.

### ELF Version

- For ELF targets, the `.type` directive is used like this:

    ```assembly
    .type *name*, *type description*
    ```

- This sets the type of symbol *name* to be either a function symbol or an object symbol.

- There are five different syntaxes supported for the *type description* field, in order to provide compatibility with various other assemblers.

- Because some of characters used in these syntaxes are comment characters for some architectures, some of the syntaxes below do not work on all architectures.

- The first variant will be accepted by the GNU assembler on all architectures.

- The syntaxes supported are:

    ```assembly
    .type <name> STT_<TYPE_IN_UPPDER_CASE>
    .type <name>, #<type>
    .type <name>, @<type>
    .type <name>, %<type>
    .type <name>, "<type>"
    ```

- The types supported are:

#### `STT_FUNC`, `function` 

- Mark the symbol as being a function name.
