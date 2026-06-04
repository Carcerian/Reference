# Master Quick Reference Card

**Ultra-fast lookup for AI developers** - One-page essential info

---

## INCLUDES TO USE

```nscript
#include "nui_api"        // NUI popups, dialogs, windows (65+ functions)
#include "cpps_api"       // CPPS placeables (50+ functions)
#include "ct_api"         // CT tailor, customization (40+ functions)
// No include needed for os_commoner.nss - attach to OnSpawn event
```

---

## MOST USED FUNCTIONS (Quick Grab)

### NUI - Show Messages/Popups
```nscript
#include "nui_api"

// Simple messages
NUI_PopupMessage(oPC, "Title", "Message");
NUI_PopupError(oPC, "Title", "Error text");
NUI_PopupSuccess(oPC, "Title", "Success text");
NUI_PopupWarning(oPC, "Title", "Warning text");
NUI_PopupInfo(oPC, "Title", "Info text");

// Interactive
NUI_PopupYesNo(oPC, "Title", "Question?");
NUI_PopupChoice(oPC, "Title", "Pick one:", "Option1|Option2|Option3");
NUI_PopupSign(oPC);  // Uses OBJECT_SELF name/description/portrait

// Custom
int nToken = NUI_DialogCreate(oPC, "Title", jContent, 1, "", "nui_handler", 4, 312.5f, 156.25f);

// Close window
NuiDestroy(oPC, nToken);
```

### CPPS - Create/Manage Placeables
```nscript
#include "cpps_api"

// Create
int nID = CPPS_PlaceableCreate(oPC, "nw_gib001", GetLocation(oPC));

// Move/Rotate/Scale
CPPS_PlaceableMove(oPC, oPlaceable, lNewLoc);
CPPS_PlaceableRotate(oPlaceable, 45.0f);
CPPS_PlaceableScale(oPlaceable, 2.0f);

// Appearance
CPPS_PlaceableSetTexture(oPlaceable, 0, "texture_resref");
CPPS_PlaceableSetColor(oPlaceable, 255, 0, 0);

// Save/Load
CPPS_PlaceableSave(oPC, oPlaceable);
CPPS_LoadAllPlaceables(GetModule());  // In module OnLoad
```

### CT - Customize Appearance
```nscript
#include "ct_api"

// Appearance
CT_AppearanceSetHead(oPC, 5);
CT_AppearanceSetBody(oPC, 3);
CT_AppearanceSetHands(oPC, 2);
CT_AppearanceSetFeet(oPC, 1);

// Colors (RGB 0-255 each)
CT_ColorSetPrimary(oPC, 255, 0, 0);    // Red
CT_ColorSetSecondary(oPC, 0, 255, 0);  // Green
CT_ColorSetTertiary(oPC, 0, 0, 255);   // Blue

// Equipment
CT_EquipmentSetAppearance(oPC, INVENTORY_SLOT_CHEST, 5);

// Save/Load
CT_AppearanceSave(oPC, "MyAppearance");
CT_AppearanceLoad(oPC, "MyAppearance");
```

### Commoner - NPC Randomization
```nscript
// Attach os_commoner.nss to NPC OnSpawn event
// Script will auto-randomize:
// - Head (race-appropriate)
// - Colors (skin, hair, tattoo)
// - Name (race/gender-appropriate)
// - Outfit (gender-specific)
// - Hand props
// - Shields

// Optional: Add local variables to NPC for customization:
// COMMONER_NO_NAME = 1          // Don't randomize name
// COMMONER_NO_COLORS = 1        // Don't randomize colors
// COMMONER_HEADS = "1 4 12"     // Custom head pool
// COMMONER_CLOTHES = "nw_cloth002 nw_cloth005"
// COMMONER_PROPS = "nw_wswdg001"
// COMMONER_SHIELDS = "none"
```

---

## WINDOW PROPERTIES (nProps)

```nscript
NUI_PROP_RESIZABLE = 1        // User can resize
NUI_PROP_COLLAPSIBLE = 2      // User can minimize
NUI_PROP_CLOSABLE = 4         // X button (most common)
NUI_PROP_BORDER = 8           // Visible border
NUI_PROP_TRANSPARENT = 16     // Transparent background

// Common combinations:
NUI_PROP_NONE = 0
NUI_PROP_CLOSABLE_ONLY = 4
NUI_PROP_CLOSABLE_TRANSPARENT = 20
NUI_PROP_ALL = 31
```

---

## JSON BUILDERS (NUI Widgets)

```nscript
// Text/Label
NuiLabel(JsonString("Text"))
NuiLabel(JsonString("Centered"), JsonInt(NUI_HALIGN_CENTER), JsonInt(NUI_VALIGN_MIDDLE))

// Button
NuiButton(JsonString("Click Me"))
NuiId(NuiButton(JsonString("Click")), "button_id")  // With ID for event handling

// Layout
NuiCol(JsonArray3(j1, j2, j3))     // Column layout with 3 items
NuiRow(JsonArray2(j1, j2))          // Row layout with 2 items

// Spacing
NuiSpacer()

// Image (use XML layout instead - see COMPILE_REFERENCE.md)

// Container
NuiWindow(jContent, JsonString("Title"), NuiRect(-1.0f, 200.0f, 312.5f, 156.25f), nProps)
```

---

## JSON CONVERSION

```nscript
JsonString("text")              // String → JSON
JsonInt(42)                     // Int → JSON
JsonBool(TRUE)                  // Bool → JSON
JsonArray1(j1)                  // 1 element
JsonArray2(j1, j2)              // 2 elements
JsonArray3(j1, j2, j3)          // 3 elements (max)
```

---

## CREATURE BODY PARTS

```nscript
CREATURE_PART_HEAD = 1
CREATURE_PART_BODY = 2
CREATURE_PART_HANDS = 3
CREATURE_PART_LEGS = 4
CREATURE_PART_FEET = 5
```

---

## COLOR SLOTS

```nscript
CREATURE_COLOR_SLOT_SKIN = 0
CREATURE_COLOR_SLOT_HAIR = 1
CREATURE_COLOR_SLOT_TATTOO_1 = 2
CREATURE_COLOR_SLOT_TATTOO_2 = 3
```

---

## EQUIPMENT SLOTS

```nscript
INVENTORY_SLOT_HEAD = 0
INVENTORY_SLOT_CHEST = 1
INVENTORY_SLOT_BOOTS = 2
INVENTORY_SLOT_ARMS = 3
INVENTORY_SLOT_RIGHTHAND = 4    // Hand props
INVENTORY_SLOT_LEFTHAND = 5     // Shields
INVENTORY_SLOT_NECK = 10
INVENTORY_SLOT_BELT = 20
```

---

## RACE TYPES

```nscript
RACIAL_TYPE_DWARF = 0
RACIAL_TYPE_ELF = 1
RACIAL_TYPE_GNOME = 2
RACIAL_TYPE_HALFELF = 3
RACIAL_TYPE_HALFLING = 4
RACIAL_TYPE_HALFORC = 5
RACIAL_TYPE_HUMAN = 6
```

---

## GENDER

```nscript
GENDER_MALE = 0
GENDER_FEMALE = 1
```

---

## COMMON PATTERNS

### Pattern 1: Create & Show Popup
```nscript
#include "nui_api"
void main() {
    object oPC = GetFirstPC();
    NUI_PopupMessage(oPC, "Title", "Hello!");
}
```

### Pattern 2: Sign Display (uses OBJECT_SELF)
```nscript
// Attach to sign OnUsed event
#include "nui_api"
void main() {
    object oPC = GetLastUsedBy();
    // Sign uses: Name (title), Description (content), Portrait (image)
    NUI_PopupSign(oPC);
}
```

### Pattern 3: Close Window
```nscript
#include "nui_api"
void main() {
    object oPC = GetFirstPC();
    int nToken = GetLocalInt(oPC, "NUI_MESSAGE_TOKEN");
    if (nToken > 0) {
        NuiDestroy(oPC, nToken);
    }
}
```

### Pattern 4: Store Data on Object
```nscript
SetLocalInt(oPC, "KEY", nValue);
SetLocalString(oPC, "KEY", sValue);
SetLocalObject(oPC, "KEY", oObject);

int n = GetLocalInt(oPC, "KEY");
string s = GetLocalString(oPC, "KEY");
object o = GetLocalObject(oPC, "KEY");

DeleteLocalInt(oPC, "KEY");
```

### Pattern 5: Loop Through Objects
```nscript
object oObj = GetFirstObjectInArea(oArea);
while (GetIsObjectValid(oObj)) {
    if (GetObjectType(oObj) == OBJECT_TYPE_CREATURE) {
        // Process creature
    }
    oObj = GetNextObjectInArea(oArea);
}
```

---

## QUICK COMPILE ERROR FIXES

| Error | Fix |
|-------|-----|
| "Unknown identifier" | Add `#include "nui_api"` or `#include "cpps_api"` or `#include "ct_api"` |
| "Declaration does not match parameters" | Check FUNCTION_INDEX.md for exact parameters |
| "No right bracket" | Add missing semicolon `;` at end of statement |
| "Parse error" | Check for missing `;` or unmatched brackets `()` `{}` `[]` |
| "Variable defined without type" | Add type: `int n = 5;` not `n = 5;` |

---

## MODULE SETUP (Required Event Hooks)

**For NUI System:**
```
Module Events:
- OnNUI Event → nui_mod_event
- Area OnEnter → nui_enter
- Area OnExit → nui_leave
- Module Load → nui_load
```

**For CPPS System:**
```
Module Events:
- Module Load → cpps_mod_load
- Module Activity → cpps_mod_act

DM Trigger:
- Placeable/Item OnUsed → cpps_conv_init
```

**For CT System:**
```
NPC Setup:
- Create "Tailor" NPC
- Conversation → ct_npc_conv
- OnSpawn → ct_npc_spawn
```

**For Commoner:**
```
NPC Setup:
- Any NPC OnSpawn → os_commoner
```

---

## FILE LOCATIONS REFERENCE

| File | Contains | Use For |
|------|----------|---------|
| FUNCTION_INDEX.md | All 155+ functions organized | Discovering what functions exist |
| COMPILE_REFERENCE.md | Error troubleshooting | Fixing compilation errors |
| README_SCRIPTS_REPO.md | System overview & integration | Understanding big picture |
| README_UTILITIES.md | Helper patterns & best practices | Creating support code |

---

## AI USAGE NOTES

**For Creating New Code:**
1. Check FUNCTION_INDEX.md for available functions
2. Copy signature from index
3. Use PATTERN section above as template
4. Add #include at top
5. Compile and test

**For Fixing Compile Errors:**
1. Read error message carefully
2. Check COMPILE_REFERENCE.md for error type
3. Look up function in FUNCTION_INDEX.md
4. Verify parameters match exactly
5. Recompile

**For Understanding Architecture:**
1. Read README_SCRIPTS_REPO.md overview
2. Check system-specific README
3. Review patterns in this card
4. Look at FUNCTION_INDEX.md organization
5. Reference COMPILE_REFERENCE.md for issues

---

**Status:** Master Quick Reference v1.0  
**Last Updated:** June 4, 2026  
**Purpose:** Fastest AI code generation & error fixing  
**Audience:** AI developers working with Carcerian systems
