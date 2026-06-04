# Compile Reference - Error Resolution Guide

Fast troubleshooting for NWScript compilation errors in Carcerian systems.

**Status:** v1.0 Complete | **Last Updated:** June 4, 2026

---

## Error Categories & Solutions

### CATEGORY: "Unknown identifier"

**Error Pattern:**
```
Error: Unknown identifier
[LINE X]: undefined_function() or undefined_constant
```

**Solutions by Type:**

#### Missing #include
```
Problem: Function used but not included
Solution: Add #include at top of script

#include "nui_api"        // For NUI functions
#include "cpps_api"       // For CPPS functions  
#include "ct_api"         // For CT functions
```

#### Wrong File Included
```
Problem: Including wrong system file
Solution: Use main API include, not utility files

DON'T USE:
#include "nui_api_popup.nss"  // ← Wrong
#include "cpps_api_funct.nss"  // ← Wrong

USE THIS:
#include "nui_api"             // ← Correct
#include "cpps_api"            // ← Correct
```

#### Typo in Function Name
```
Problem: NUI_PopupMessag instead of NUI_PopupMessage
Solution: Match exact function name from FUNCTION_INDEX.md

Check: FUNCTION_INDEX.md → NUI System → Message Functions
```

---

### CATEGORY: "Declaration Does Not Match Parameters"

**Error Pattern:**
```
Error: DECLARATION DOES NOT MATCH PARAMETERS
[LINE X]: FunctionName(param1, param2, ...)
```

**Common Causes & Fixes:**

#### Wrong Parameter Type
```
Problem: NUI_PopupMessage(oPC, 123, "text")  // 123 is int, should be string
Solution: NUI_PopupMessage(oPC, "Title", "Message")

Reference: FUNCTION_INDEX.md
  NUI_PopupMessage | (oPC, sTitle, sMessage, ...) | int | nui_api_popup.nss
                       ↑      ↑       ↑
                    object  string  string
```

#### Missing Required Parameter
```
Problem: NUI_PopupMessage(oPC, "Title")  // Missing sMessage
Solution: NUI_PopupMessage(oPC, "Title", "Message")
```

#### Wrong Parameter Count
```
Problem: CPPS_PlaceableMove(oPC, oPlaceable)  // Missing location
Solution: CPPS_PlaceableMove(oPC, oPlaceable, lNewLoc)

From FUNCTION_INDEX.md:
  CPPS_PlaceableMove | (oPC, oPlaceable, lNewLoc) | int | cpps_api.nss
                       3 required parameters ↑
```

#### JSON Type Mismatch
```
Problem: NuiButton("Button")  // Should return json
Solution: NuiButton(JsonString("Button"))

Check: These need JsonString wrapper:
  - JsonString(s)
  - JsonInt(n)
  - JsonBool(b)
```

---

### CATEGORY: "No Right Bracket On Expression"

**Error Pattern:**
```
Error: NO RIGHT BRACKET ON EXPRESSION
[LINE X]: [Complex expression]
```

**Solutions:**

#### Missing Semicolon
```
Problem: if (nValue > 5)
            NUI_PopupMessage(oPC, "Title", "Message")
         // ↑ Missing semicolon

Solution: NUI_PopupMessage(oPC, "Title", "Message");
```

#### Mismatched Brackets/Parentheses
```
Problem: NuiCol(JsonArray2(NuiLabel(...), NuiButton(...))
                          ↑ Missing closing parenthesis

Solution: NuiCol(JsonArray2(NuiLabel(...), NuiButton(...)))
                           ↑                           ↑
                        Should match
```

#### Function Call Inside Function Missing Semicolon
```
Problem: void main()
{
    NUI_PopupMessage(oPC, "Title", "Message")  // ← Missing semicolon
    // Next line
}

Solution: NUI_PopupMessage(oPC, "Title", "Message");
```

---

### CATEGORY: "Parse Error"

**Error Pattern:**
```
Error: PARSE ERROR [ERROR_CODE]
[LINE X]: Unexpected token
```

**Common Issues:**

#### Invalid Local Variable Syntax
```
Problem: object oPC = GetFirstPC;  // Missing parentheses
Solution: object oPC = GetFirstPC();

Problem: SetLocalInt(oPC, "KEY", nValue)  // ← Missing semicolon
Solution: SetLocalInt(oPC, "KEY", nValue);
```

#### Invalid Include Syntax
```
Problem: #include nui_api        // ← No quotes
Solution: #include "nui_api"

Problem: #include "nui_api.nss"  // ← Don't include .nss
Solution: #include "nui_api"
```

#### Invalid String Concatenation
```
Problem: string s = "Text" + IntToString(5) + "More"  // ← No + operator for strings
Solution: string s = "Text" + IntToString(5) + "More";  // Actually works but check context

Problem in assignment: SetName(oPC, "Name" + IntToString(nID))
Solution: SetName(oPC, "Name" + IntToString(nID));
```

---

### CATEGORY: "Variable Defined Without Type"

**Error Pattern:**
```
Error: VARIABLE DEFINED WITHOUT TYPE
[LINE X]: variable_name = value
```

**Solutions:**

#### Missing Type Declaration
```
Problem: nValue = 5;  // Type not declared
Solution: int nValue = 5;

Problem: oPC = GetFirstPC();  // Type not declared
Solution: object oPC = GetFirstPC();
```

#### Wrong Syntax in Declaration
```
Problem: GetLocalInt oPC, "KEY";  // ← Missing parentheses
Solution: int nValue = GetLocalInt(oPC, "KEY");
```

#### Const Declaration Error
```
Problem: const NUI_PROP_CLOSABLE = 4;  // ← Missing type
Solution: const int NUI_PROP_CLOSABLE = 4;
```

---

### CATEGORY: "Function Expected"

**Error Pattern:**
```
Error: FUNCTION EXPECTED
[LINE X]: statement_that_looks_like_call
```

**Solutions:**

#### Missing Function Name
```
Problem: (oPC, "Title", "Message");  // ← Missing function name
Solution: NUI_PopupMessage(oPC, "Title", "Message");
```

#### Invalid Function Call Position
```
Problem: int n = GetFirstPC();  // Calling in assignment (void function)
Solution: object oPC = GetFirstPC();  // GetFirstPC returns object

Check return type in FUNCTION_INDEX.md
```

#### Malformed Array
```
Problem: JsonArray(1, 2, 3)  // ← No JsonArray function
Solution: JsonArray3(j1, j2, j3)  // Use JsonArray1, 2, or 3

From FUNCTION_INDEX.md:
  JsonArray1 - one element
  JsonArray2 - two elements  
  JsonArray3 - three elements
```

---

## Quick Diagnostic Checklist

### For Any Compilation Error:

1. **Check Include Files**
   ```
   #include "nui_api"        // For NUI
   #include "cpps_api"       // For CPPS
   #include "ct_api"         // For CT
   ```

2. **Verify Function Name**
   - Use FUNCTION_INDEX.md
   - Check exact spelling
   - Verify it exists in correct system

3. **Check Parameter Count**
   - Count parameters in your call
   - Compare to FUNCTION_INDEX.md signature
   - Look for optional parameters `[]`

4. **Verify Parameter Types**
   ```
   (object, string, string) for NUI_PopupMessage
   (object, string, location) for CPPS_PlaceableMove
   (object, int) for CT_AppearanceSetHead
   ```

5. **Check Semicolons**
   - All statements need `;` at end
   - Before `}`
   - After function calls

6. **Check Brackets/Parentheses**
   - All `(` need matching `)`
   - All `{` need matching `}`
   - All `[` need matching `]`

---

## System-Specific Common Errors

### NUI Errors

#### "NUI_PopupMessage not found"
```
Solution: #include "nui_api"
          at top of script
```

#### "JsonString not found"
```
Solution: This is built-in NWScript function
          Make sure #include "nui_api" present
          It includes nw_inc_nui.nss
```

#### "NuiDestroy takes wrong parameters"
```
Problem: NuiDestroy(nToken);  // Missing oPC
Solution: NuiDestroy(oPC, nToken);
```

#### "Window won't appear"
This is RUNTIME error, not compile error
Check: Module OnNUI event hook → nui_mod_event

### CPPS Errors

#### "CPPS_PlaceableCreate not found"
```
Solution: #include "cpps_api"
          at top of script
```

#### "location type not recognized"
```
Check: Make sure location variable is initialized
       location lLoc = GetLocation(oPC);
```

### CT Errors

#### "CT_AppearanceSetHead not found"
```
Solution: #include "ct_api"
          at top of script
```

#### "Color parameters wrong"
```
Problem: CT_ColorSetPrimary(oPC, nColor)
Solution: CT_ColorSetPrimary(oPC, nRed, nGreen, nBlue)
          // Three separate int parameters (0-255 each)
```

### Commoner Errors

#### "os_commoner compiles but does nothing"
This is expected - it's an OnSpawn script

Solution: Attach to NPC OnSpawn event:
1. Select NPC
2. Properties → Events
3. Set OnSpawn → os_commoner
4. Recompile

---

## Include File Reference

### What Each File Contains

**nui_api.nss** (Main entry)
- Includes all NUI systems
- Use this: `#include "nui_api"`

**cpps_api.nss** (Main entry)
- Includes all CPPS systems
- Use this: `#include "cpps_api"`

**ct_api.nss** (Main entry)
- Includes all CT systems
- Use this: `#include "ct_api"`

**nui_api_popup.nss** (Don't include directly)
- Popup functions (included by nui_api.nss)

**nui_api_config.nss** (Don't include directly)
- Constants (included by nui_api.nss)

**os_commoner.nss** (Standalone)
- Attach to OnSpawn event
- Don't include in other files

---

## Compilation Success Checklist

Before assuming error is in your code:

✓ All #include statements are correct and in quotes  
✓ All function names match FUNCTION_INDEX.md exactly  
✓ All parameter counts match FUNCTION_INDEX.md  
✓ All parameter types match (object vs string vs int vs json vs location)  
✓ All statements end with semicolon  
✓ All parentheses/brackets are balanced  
✓ No circular includes  
✓ No missing includes  

---

## Error Message Examples & Solutions

### Example 1: Popup Won't Compile
```
Error: Unknown identifier NUI_PopupMessage
Line: nToken = NUI_PopupMessage(oPC, "Title", "Message");

Solution:
Add to top of script:
#include "nui_api"
```

### Example 2: Parameter Mismatch
```
Error: DECLARATION DOES NOT MATCH PARAMETERS
Line: CPPS_PlaceableMove(oPC, oPlaceable);

Solution:
From FUNCTION_INDEX.md: CPPS_PlaceableMove needs 3 parameters
Correct: CPPS_PlaceableMove(oPC, oPlaceable, lNewLoc);
```

### Example 3: Missing Semicolon
```
Error: NO RIGHT BRACKET ON EXPRESSION
Line: NUI_PopupMessage(oPC, "Title", "Message")

Solution:
Add semicolon:
NUI_PopupMessage(oPC, "Title", "Message");
```

### Example 4: Wrong Parameter Type
```
Error: DECLARATION DOES NOT MATCH PARAMETERS
Line: NUI_PopupMessage(oPC, 123, "Message");

Solution:
Second parameter must be string, not int:
NUI_PopupMessage(oPC, "Title", "Message");
```

---

## When Stuck

1. **Check FUNCTION_INDEX.md** - Exact function signature
2. **Count parameters** - Are they all there?
3. **Check types** - Match FUNCTION_INDEX.md
4. **Check includes** - Is system included?
5. **Check syntax** - Semicolons, brackets, parentheses
6. **Compile again** - Try recompiling
7. **Check line number** - Error on that exact line?

---

## Key Rules

### Always Remember:
- Functions need parentheses: `GetFirstPC()` not `GetFirstPC`
- Statements need semicolons: `SetName(oPC, "Name");`
- Includes need quotes: `#include "nui_api"`
- Includes don't need .nss: `#include "nui_api"` not `"nui_api.nss"`
- Variables need types: `int n = 5;` not `n = 5;`
- Constants need types: `const int X = 1;` not `const X = 1;`

---

**Status:** Complete v1.0 Error Reference  
**Last Updated:** June 4, 2026
