---
author: Argald0
alias: md-cheat, markdown-cheatsheet
---

# Markdown cheatsheet

## 1. Formatting
```
_Italic_  
*Italic*  
__Bold__  
**Bold**  
_You **can** combine them_  
~~Strikethrough~~  
Example<sup>superscript</sup>  
Example<sub>subscript</sub>  
```
_Italic_  
*Italic*  
__Bold__  
**Bold**  
_You **can** combine them_  
~~Strikethrough~~  
Example<sup>superscript</sup>  
Example<sub>subscript</sub>


---
## 2. Lists

=== "Unordered lists"

    ```md
    - Unordered list
    + Unordered list
    * Unordered list
    - Nested
        - Unordered
        - List
    ```

    - Unordered list
    + Unordered list
    * Unordered list
    - Nested
        - Unordered
        - List

=== "Ordered lists"

    ```md
    1. Ordered list
    2. Ordered list
    3. Nested
       1. Ordered
       2. List
    ```

    1. Ordered list  
    2. Ordered list
    3. Nested
        1. Ordered
        2. List


---
## 3. Tasks

```md
+ [x] #tags, [links](), **formatting** supported
* [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
- [ ] tasks can be clicked in Preview to be checked off
	- [ ] nested tasks
```

+ [x] #tags, [links](), **formatting** supported
* [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
- [ ] tasks can be clicked in Preview to be checked off
	- [ ] nested tasks

---
## 4. Links

#### 4.1. External links

```md
<https://obsidian.md>   
<other@fake.mail>  
```

<https://obsidian.md>   
<other@fake.mail>  

#### 4.2. Internal links

```md
[Networking](<practical_ethical_hacking/peh-networking.md>)
```

[Networking](<practical_ethical_hacking/peh-networking.md>)

---
## 5. Images

=== "Local picture with caption"

    ```md
    <figure>
        <img src="../images/argald0_logo.png" width="300" />
        <figcaption>My logo caption</figcaption>
    </figure>
    ```

    <figure>
        <img src="../images/argald0_logo.png" width="300" />
        <figcaption>My logo caption</figcaption>
    </figure>

=== "Online picture aligned right"

    ![Image](<https://static-s.aa-cdn.net/img/ios/1165192859/5ac4c0723f8587cbf39f44583f4a7012>){align=right}

    ```md
    ![Image](<https://full/path/to/picture>){align=right}
    ```

---
## 6. Tables

```md
header 1|header 2|header 3
:---|:---:|---:
-|-|-
align left | center | align right
```

header 1|header 2|header 3
:---|:---:|---:
-|-|-
align left | center | align right

---
## 7. Math

```md
$\varphi^{\theta\to2}_{3}$  

$\begin{vmatrix}a & b\\
c & d
\end{vmatrix}=ad-bc$  

$\frac{\frac{x}{1}}{x - y}$
```

$\varphi^{\theta\to2}_{3}$  

$\begin{vmatrix}a & b\\
c & d
\end{vmatrix}=ad-bc$  

$\frac{\frac{x}{1}}{x - y}$

---
## 8. Blockquotes

```md
> Tu ne sais pas ce que le futur nous attend.

\- Massian Chakir, 2015
```

> Tu ne sais pas ce que le futur nous attend.

\- Massian Chakir, 2015

---
## 9. Code

#### 9.1. Inline code

```md
Text inside `backticks` on a line will be formatted like code.
```

Text inside `backticks` on a line will be formatted like code.

#### 9.2. Code blocks

    ``` python linenums="2" hl_lines="2 4"
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]
    ```

``` python linenums="2" hl_lines="2 4"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

#### 9.3. Indented text

```md
    Text indented with a tab is formatted like this, and will also look like a code block in preview.
```

    Text indented with a tab is formatted like this, and will also look like a code block in preview.

#### 9.4. Tabbed Codeblocks

    === "C"

        ``` c
        #include <stdio.h>

        int main(void) {
        printf("Hello world!\n");
        return 0;
        }
        ```

    === "C++"

        ``` c++
        #include <iostream>

        int main(void) {
        std::cout << "Hello world!" << std::endl;
        return 0;
        }
        ```

!!! warning "Tabbed Codeblocks"
    === "C"

        ``` c
        #include <stdio.h>

        int main(void) {
        printf("Hello world!\n");
        return 0;
        }
        ```

    === "C++"

        ``` c++
        #include <iostream>

        int main(void) {
        std::cout << "Hello world!" << std::endl;
        return 0;
        }
        ```

---
## 10. Admonition

```md
!!! note "Phasellus posuere in sem ut cursus"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

!!! note "Phasellus posuere in sem ut cursus"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

---
## 11. Pagebreak

```html
<div style="page-break-after: always;"></div>
```

---
## 	$\infty$. Source 

[Writing Mathematic Fomulars in Markdown](<https://csrgxtu.github.io/2015/03/20/Writing-Mathematic-Fomulars-in-Markdown/>)  
[Obsidian official page : Format your notes](https://publish.obsidian.md/help/How+to/Format+your+notes)  
[Mermaid JS : Sequence Diagram](https://mermaid-js.github.io/mermaid/#/sequenceDiagram)  