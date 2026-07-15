# Reasoning

| Deductive Reasoning                                                         | Inductive Reasoning                             |
| --------------------------------------------------------------------------- | ----------------------------------------------- |
| Valid or Invalid                                                            | Strong or Weak                                  |
| 100% true or false                                                          | Probable and not probable                       |
| very sure as long as premises are true.                                     | cant make strong claims just general direction. |
| sound argument as long as all premises are true otherwise unsound argument. | cogent vs not cogent.                           |

Premise = Core Fundamental True Facts.



## Frameworks

IF → THEN → THEREFORE

* **IF** these conditions are true
* **THEN** this must happen
* **THEREFORE** we conclude/implement this

Example:

* IF an employee clocks more than 8 hours
* THEN overtime rules apply
* THEREFORE the system must calculate overtime pay



### MECE (Mutually Exclusive, Collectively Exhaustive)

When breaking down requirements, always ask:

* Did I split everything into **non-overlapping parts**?
* Did I include **all possible cases**?

Example (attendance rules):

* Present
* Sick leave
* Vacation
* Missing punch

If something overlaps (e.g., “late + absent”), your logic is not clean yet.





***

### Exceptions

Every requirement has two layers:

1. **Happy path (normal case)**
2. **Exceptions (what breaks it)**

Example:

* Happy path: employee works scheduled shift → normal pay
* Exception: overtime, absence, shift swap, public holiday

If you can’t list exceptions, you don’t fully understand the requirement yet.





***

### 4. The “Explain it to a 12-year-old” filter

After you understand something, force yourself to restate it:

* No jargon
* No abbreviations
* One idea per sentence

If it becomes unclear when simplified, that means your understanding is still incomplete.

***

### 5. The “decomposition ladder”

Break problems down in levels:

1. System goal
2. Process
3. Rule
4. Data input/output
5. Edge cases

Example:

* Goal: calculate payroll correctly
* Process: collect time data
* Rule: apply overtime logic
* Data: hours worked, contract type
* Edge cases: missing punches, holidays

This is extremely useful in ERP / SAP / ASES-type environments.

***

### 6. Communication trick: “headline → detail → example”

When explaining:

* **Headline:** what it is
* **Detail:** how it works
* **Example:** concrete case



{% hint style="info" icon="eye" %}
aggressively looking for what must be true, and what is missing.
{% endhint %}
