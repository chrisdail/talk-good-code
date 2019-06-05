name: heading
layout: true
class: center, middle, inverse

---

# The Good Code

Chris Dail - [@chrisdail](https://twitter.com/chrisdail)

Senior Director, Software Engineering at [Akiri](https://akiri.com)

---

background-image: url(images/wtfs-per-min.png)

---

# The Good Code

Chris Dail - [@chrisdail](https://twitter.com/chrisdail)

Senior Director, Software Engineering at [Akiri](https://akiri.com)

---

# Once Upon a Time

---

layout: false

# Not Good Code

- Repeated Code - Functions?
- Right Tool for the Job - Not Bash!
  - Consider Python - `requests` and `json`
  - Avoid and Handle Errors

---

background-image: url(images/one_week_later.png)

---

background-image: url(images/three_weeks_later.jpg)

---

template: heading
background-image: url(images/mind_blown.jpg)

---

background-image: url(images/this_bad_code.jpg)
template: heading
![:scale 100%]()

---

template: heading

# Welcome!
# Everything is fine.

---

template: heading

# Why is Good Code
# Important?

---

layout: false

# Bad Code

- Decreases productivity over time
- Hard to maintain
--

- Broken Window Affect
  - Bad code causes carelessness
  - Leads to more bad code

---

template: heading
# Good Code Makes
# Happy Coders

---

template: heading
# Qualities of Good Code

---

template: heading
# Readability

---

# Readability

- Other People
- Reading vs Writing Code

---

# Simple

- Easily Understood
- Simple Architecture, Abstractions
- One Thing does One Thing

---

template: heading
# No Suprises

---

template: heading

# Deadlines...
## Fix in the Next Release

---

# You Will Never Come Back

- Get it Right the First Time

--
- 'Grand Redesign' that never comes
- Code Reviews: Don't let poor code slip through

---

# Quantity and Quality

- Industry average is around 15-50 bugs per 1000 lines of code
--

- Writing less code will result in fewer bugs #HeDidTheMath
--

- Cannot do this artificially
  - **Readability!**
  - Quality - Fewer lines, more meaningful
  - Simple

---

template: heading
# Meaningful Naming

---

class: bad

# Naming

- Reveal Intent - what is this thing used for?
```
AccountPrincipal p;
```
--
- Meaningful distinctions, avoid "noise words" redundant
```
RestClient clientToUse = getClient();
```
--
- Human readable / searchable - No per character cost
```
String acctNm
```
--
- Follow standards: like javabean naming in Java.

---

# Naming

- Classes/Types: Nouns, meaningful and avoid fluff words
.good[
```
Account
Alert
DailyUsage
AuthorizationPolicy
```
]
.bad[
```
SystemData
ConfigInfo
Manager
Util
```
]

---

# Naming

- Methods/Functions: Verbs. Function names descriptive and don't be afraid of length
.good[
```
process()
startMonitor()
modifyAccount()
runPlaybookAndWaitComplete()
```
]
.bad[
```
varsWithTarget()
taskStatusInProgress()
```
]

---

class: bad

# Naming - Avoid Encodings

- Avoid encoding names with: Type, Scope, Visibility or Static
    - Hungarian Notation
- This is what we have IDEs and syntax highlighting for

```
ListBox lb_name
private static Logger _log;
private m_name;
Integer nSize;
List<User> usersList;
```

---

# Naming - Libraries / Modules

- Top 5 worst modules names
--

  - `utils`
  - `commons`
  - `shared`
  - `lib`
  - `tools`
--

- Alternatives
  - `io`
  - `config`
  - `encryption`

---

class: bad

# Functions

- Should do **one** thing and only one thing
```
private void validateAndExtractInformationFromZip()
```
--
- Be wary of **and** in function names
- You can always call another function
--

- Should be short (Keep under 20 lines in most cases)
- Avoid side effects (getName should not change state)

---

class: bad

# Classes and Objects

- Classes should also **Do One Thing**
- Single Level of Abstraction
--

- Properties and functions follow the "theme"
--

- Avoid "Junk Drawer" classes

---

# Magic Numbers

- Avoid magic numbers or magic strings
- Use constants defined in one place

.bad[
```
if ((i == 0) &&
    !((attVal.charAt(i) >= 1 && attVal.charAt(i) <= 31)
    || (attVal.charAt(i) == 33)
    || (attVal.charAt(i) >= 36 && attVal.charAt(i) <= 42)
    || (attVal.charAt(i) >= 45 && attVal.charAt(i) <= 58)
    || (attVal.charAt(i) == 61)
    || (attVal.charAt(i) >= 63 && attVal.charAt(i) <= 91)
    || (attVal.charAt(i) >= 93)
```
]
--

.bad[
```
const val NUMBER_33 = 33
```
]
--
.good[
```
const val ASCII_CHAR_EXCLAMATION = 33
```
]

- Enhance Readability

---

# Comments

- Explain **intent** of the code
- Answer **Why** not **What** or **How**
--

- Add comments only when it enhances readability
--

- If you need to explain your code, maybe the code is not clear?
--

- Use TODOs sparingly

---

class: bad

# Avoid Comments That Are

- Redundant - Is it saying the same thing as the code?
```
    // Checks for null
    if (state == null) {
        return null; // XXX
    }
```
```java
    /**
      * Construct an account chargeback context.
      *
      * @param   name    The account name
      * @param   id      The account ID
      */
    public AccountChargeback(String name, String id) {
        super(name, id);
    }
```

---

class: bad

# Avoid Comments That Are

- Misleading
```
    // Check to see if the order is valid.
    // Returns true for valid, false for invalid
    public boolean validateOrder(Order order) {
        if (!order.isValid()) {
            throw new ValidationException("Order is not valid");
        }
        return true;
    }
```
--
- Commented Out Code - Version control history
--

- References to bug numbers - Also, version control history
```
// fix for CP-1234
if (state == null) {
```

---

# Version Control

- Version Control History should be treated like **code**
- Readability is important
- Should read like a story
--

- Good Commit comments
- Small commits
- Small pull requests

---

# Formatting

- Keep files short (Typically less than 300 lines)
- Keep line length short (<120 characters)
- Maximum of 2 levels of indenting in a function in most cases
- Use whitespace to separate 'paragraphs' of code
- Variables declared close to usage as possible
- Instance variables at the top of the class

---

# Error Handling

- Exceptions should be exceptional
--

- Behave in reasonable ways over throwing errors
  - Consider Empty list to show no results
--

- Early return for invalid cases (bouncer pattern)
- No exception swallowing (empty catch block)

---

template: heading

# Scout Rule
--

## Leave the code better than you found it

---

template: heading
background-image: url(images/when-in-rome.jpg)

---

# When in Rome

- Follow the code style of the codebase you are in
- Follow the conventions of the language
--

- CamelCase vs snake_case
- Tabs vs Spaces
- Be consistent
--

- If you need to reformat code, do so in a standalone commit

---

# DRY - Don't Repeat Yourself

> "Every piece of knowledge must have a single unambiguous, authoritative representation within a system" - Pragmatic Programmer
--

- Don't Repeat Yourself
--

- Reuse code - Functions, Libraries
- Redundant comments
--

- Multiple developers teams
  - Duplication of validation/util functions
  - Centralize and Make reuse easy
  - Look for existing code before your write

---

template: heading
background-image: url(images/copy-paste.jpg)

---

# Copy and Paste

- Most evil of programming techniques
- Creates Repetition
--

- Fix bugs in multiple places
--

- You may not fully understand the code being copied
--

- Consider reuse with functions instead

---

# Clever Code

- Be wary of "clever" code (aka "cute", "magic")
--

- Solutions that are not intuitive may be harder to read
- Sometimes the more dull, straightforward way is better
--

- Keep in mind the programming level of your team

---

template: heading
# Why is it hard to
# Write Good Code?

---

background-image: url(images/computational_thinking.jpg)

---

template: heading

# Good Code Is
# More Art that Math

---

template: heading

# Good Code
# Tells a Story

---

template: heading

# Questions

---

template: heading

# Bonus!

---

# Reinventing the Wheel

- Consider open source packages over rolling your own
- Ask if this library is part of your core competencies
- All code is a liability you need to maintain
- Get over your pride
  - You may be able to build a great search engine
  - Your time may be better used elsewhere

---

# Using Third Party / Open Source Packages

- As few dependencies as required to do the task
- Favor using tools you already have
- Choose the right tool for the job
  - How much code do I need to use this?
  - bash/sed/awk are poor json parsers
- Fork wisely. Fork only if needed and do it right
  - Avoid cherry-picking and committing modified files

---

# Reading List

- Clean Code - Robert C. Martin
- The Pragmatic Programmer - Andrew Hunt, David Thomas
- Code Complete - Steve McConnell
