# TransistorTables
Truth tables for all the transistors used in the adder.

A guide to my ternary logic system:

HIGH charge = TRUE = 2<br>
MEDIUM charge = UNCERTAIN = 1<br>
LOW charge = FALSE = 0<br>

Each gate is represented by its circuit diagram notation along with either the letters "K", "B", or "T". These stand for "Kleene", "Binary", and "Ternary" respectively. The notations will either pin them as OR, AND, NOR, or NAND-based. A rundown of what each letter means is detailed below.

<b>Kleene Logic:</b>
My ternary adder takes heavy influence from "Kleene Logic", a base-3 interpretation of Boolean Logic, in which there exists an "uncertain" value. Two Kleene gates are used, KOR and KAND (Kleene OR and Kleene AND). More information on Kleene Logic can be found in the "Sources" readme.

<b>Binary:</b>
Unfortunately, Kleene Logic on its own does not allow for clever manipulation of a MEDIUM charge. For example, in each Kleene Logic gate, a MEDIUM charge will always be returned if both input charges are also MEDIUM. Trying to invert any of them is pointless as NOT 1 is still 1. As one may imagine, this causes problems when a ternary adder needs to output 2 if both inputs are 1.
So, I considered the implementation of binary logic into the ternary system. These transistors can take only two inputs. Their physical design would interpret any MEDIUM charge (ie. 1) as either a HIGH charge (ie. 2) or a LOW charge, depending on the gate. The two gates, BAND and BOR (Binary NAND and Binary NOR) function exactly the same as they do in a binary circuit. The only difference is that the TRUE value is 2 instead of 1.

<b>Ternary:</b>
That being said, we <i>still</i> have some issues. The adder still needs to output 1 if both inputs are 2. This is simply impossible using all four gates mentioned above, since the output would either be 0 or 2. No amount of combination of those gates simply will not work.
To work around this, I devised a variation of the binary gates mentioned above. The Ternary gates TAND and TOR (Ternary NAND and Ternary NOR) are identical to their BAND and BOR counterparts, but instead of outputting a HIGH charge where the output is TRUE, it returns a MEDIUM charge. This does not follow any rules within Boolean or Kleene Logic, but are nonetheless needed for the adder to function.
