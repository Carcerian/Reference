# Scripts - Utilities & Support

A collection of utility scripts, helper functions, and support code for NWN:EE development. These scripts provide foundational functionality, common patterns, and reusable components that support larger systems.

## Overview

The Scripts Utilities section contains standalone scripts and utility code designed to be integrated into your own projects. These are building blocks, helpers, and common-use scripts rather than complete systems.

**Content Type:** Utilities, helpers, templates, common patterns  
**Language:** NWScript (100% NWN:EE)  
**Focus:** Reusable code, best practices, foundational patterns

## Script Categories

### Core Utilities

Fundamental utility scripts used across multiple systems.

**String & Text Processing**
- Text parsing helpers
- String manipulation functions
- Name generation utilities
- Format & conversion tools

**Data Management**
- Local variable wrappers
- Data structure helpers
- Stack/queue implementations
- Cache management

**Math & Calculations**
- Vector operations
- Distance & geometry
- Random number helpers
- Probability functions

**Logging & Debugging**
- WriteTimestampedLogEntry wrappers
- Debug output helpers
- Error tracking
- Performance monitoring

### Event Handlers

Common event handler scripts and patterns.

**Module Events**
- Module load/unload handlers
- Module chat handlers
- Module heartbeat utilities
- Event dispatcher patterns

**Area Events**
- Area enter/exit handlers
- Area cleanup scripts
- Spawn/despawn management
- Activity tracking

**Object Events**
- Creature death handlers
- Inventory management
- Conversation callbacks
- Animation completion

**Combat Events**
- Damage calculation helpers
- Combat round utilities
- Action resolution
- Effect management

### Data Structures

Implementations of common data structures in NWScript.

**Lists & Collections**
- Integer lists (IList)
- String lists (SList)
- Object lists (OList)
- Associative arrays/maps

**Stacks & Queues**
- First-in-first-out (FIFO)
- Last-in-first-out (LIFO)
- Priority queues
- Deques (double-ended)

**Trees & Graphs**
- Binary tree implementations
- Tree traversal utilities
- Graph navigation
- Pathfinding helpers

### Time & Scheduling

Time-based utilities and scheduling helpers.

**Timing Functions**
- Millisecond precision timers
- Game-time conversions
- Real-time tracking
- Elapsed time calculations

**Scheduled Tasks**
- Task scheduler
- Delay command wrappers
- Event timing
- Interval execution

**Calendar Utilities**
- Game calendar conversions
- Day/night detection
- Season tracking
- Holiday management

### Location & Movement

Spatial and movement-related utilities.

**Vector Math**
- 3D vector operations
- Direction calculations
- Distance measurement
- Line intersection

**Pathfinding**
- Waypoint helpers
- Path validation
- Obstacle detection
- Movement utilities

**Area Navigation**
- Area boundary detection
- Location validation
- Coordinate conversion
- Spatial queries

### Item & Inventory

Item management and inventory utilities.

**Item Helpers**
- Item property wrappers
- Item cost calculation
- Value assessment
- Quality assessment

**Inventory Management**
- Inventory queries
- Item movement
- Container utilities
- Weight calculation

**Equipment System**
- Armor class calculation
- Bonus aggregation
- Restriction checking
- Compatibility validation

### Combat & Damage

Combat-related utility functions.

**Damage Calculation**
- Damage type handling
- Resistance/vulnerability
- Save calculation
- Effect resolution

**Combat Resolution**
- Attack roll helpers
- Hit testing
- Damage application
- Effect stacking

**Combat Status**
- Condition tracking
- Status effect management
- Buff/debuff utilities
- Duration tracking

### NPC & Creature

NPC and creature management utilities.

**Creature Helpers**
- Ability score wrappers
- Skill calculation
- Feat checking
- Class helpers

**NPC Management**
- Conversation triggers
- AI state management
- Relationship tracking
- Faction helpers

**Henchman Utilities**
- Henchman state
- Control helpers
- Experience sharing
- Loyalty tracking

### Player Utilities

Player-specific helper functions.

**Player Information**
- Level/experience helpers
- Class information
- Race/gender utilities
- Property queries

**Player State**
- Rest tracking
- Death state
- Combat status
- Movement state

**Party Management**
- Party queries
- Member utilities
- Experience distribution
- Loot sharing

### Conversation Helpers

Conversation system utilities.

**Dialog Navigation**
- Node traversal
- Branch detection
- Reply counting
- Dialog state

**Speech Handling**
- Speaker identification
- Speech recording
- Conversation history
- Dialog logging

**Response Processing**
- Reply parsing
- Action resolution
- Branching logic
- Conditional responses

## Common Patterns

### Error Handling Pattern

```nscript
// Check for error condition
if (!ValidateInput(nValue))
{
    // Log error
    WriteTimestampedLogEntry("error.log", "Invalid input: " + IntToString(nValue));
    // Return error code
    return ERROR_INVALID_INPUT;
}
// Continue processing
return SUCCESS;
```

### Local Variable Management

```nscript
// Store data on object
SetLocalInt(oObject, "DATA_KEY", nValue);
SetLocalString(oObject, "NAME_KEY", sValue);
SetLocalObject(oObject, "OBJECT_KEY", oOther);

// Retrieve data
int nData = GetLocalInt(oObject, "DATA_KEY");
string sData = GetLocalString(oObject, "NAME_KEY");
object oData = GetLocalObject(oObject, "OBJECT_KEY");

// Clean up
DeleteLocalInt(oObject, "DATA_KEY");
```

### Loop Patterns

```nscript
// Creature in area iteration
object oCreature = GetFirstObjectInArea(oArea);
while (GetIsObjectValid(oCreature))
{
    if (GetObjectType(oCreature) == OBJECT_TYPE_CREATURE)
    {
        // Process creature
        ProcessCreature(oCreature);
    }
    oCreature = GetNextObjectInArea(oArea);
}
```

### DelayCommand Usage

```nscript
// Execute after delay (in seconds)
DelayCommand(2.0, DoSomething());

// Avoid using with void functions
DelayCommand(1.0, DeleteObject(oObject));

// Create wrapper for complex operations
void DelayedAction()
{
    // Complex operation here
}
DelayCommand(1.0, DelayedAction());
```

## Best Practices

### Code Organization

- Keep functions focused and single-purpose
- Use clear, descriptive naming
- Group related functions together
- Include header comments for all functions

### Performance

- Avoid loops in frequently-called functions
- Cache values that don't change
- Use DelayCommand for expensive operations
- Minimize string concatenation in loops

### Reliability

- Always validate input parameters
- Check object validity before use
- Handle null/invalid cases explicitly
- Log errors for debugging

### Maintainability

- Comment complex logic
- Use consistent naming conventions
- Document parameter requirements
- Provide usage examples

## Integration Guide

### Using Utilities in Your Scripts

1. **Copy utility script** to your module scripts directory
2. **Include at top** of your script:
   ```nscript
   #include "utility_name"
   ```
3. **Use functions** from utility
4. **Follow patterns** shown in documentation

### Combining Multiple Utilities

```nscript
#include "string_helpers"
#include "math_helpers"
#include "location_helpers"

void main()
{
    // Use functions from all three utilities
    string sFormatted = FormatString("Health: %i", nHP);
    float fDistance = CalculateDistance(lLoc1, lLoc2);
    location lNew = GetLocationInDirection(lStart, fDistance, fAngle);
}
```

## Common Functions Reference

### String Functions
```nscript
string TrimString(string sString);
int CountSubstring(string sString, string sFind);
string ReplaceString(string sString, string sFind, string sReplace);
string ToLower(string sString);
string ToUpper(string sString);
```

### Math Functions
```nscript
float Distance(location l1, location l2);
float AbsoluteValue(float fValue);
int MinValue(int n1, int n2);
int MaxValue(int n1, int n2);
int Clamp(int nValue, int nMin, int nMax);
```

### Object Functions
```nscript
int CountObjectsInArea(object oArea, int nType);
object GetNearestCreature(int nType, object oReference);
int GetObjectDistance(object o1, object o2);
void DestroyAllObjects(object oContainer, int nType);
```

### Inventory Functions
```nscript
int CountItemsOfType(object oContainer, string sItemType);
object GetItemByTag(object oContainer, string sTag);
int GetTotalItemValue(object oContainer);
void RemoveAllItems(object oContainer);
```

### Time Functions
```nscript
int GetGameHour();
int GetGameDayOfMonth();
string GetCurrentGameTime();
int CalculateGameMinutes(int nRounds);
```

## Troubleshooting

### Common Issues

**"Unknown identifier" error:**
- Verify #include statement is present
- Check script is in scripts directory
- Ensure correct script name in include

**Function not found:**
- Check function exists in utility script
- Verify function signature matches
- Check parameter types match

**Script won't compile:**
- Review compiler error message
- Check for circular includes
- Verify all dependencies present

**Function behaves unexpectedly:**
- Verify input parameters are valid
- Check documentation for edge cases
- Review function implementation
- Test with simple example first

## Contributing

Found a useful utility script? Want to contribute?

### Guidelines
1. Write clean, well-commented code
2. Include documentation with examples
3. Follow NWScript best practices
4. Test thoroughly
5. Submit with clear description

### Process
1. Create script following standards
2. Include header documentation
3. Add usage examples
4. Test in NWN:EE
5. Submit via pull request

## Testing Scripts

### Test Template

```nscript
// Test script to verify utility functions
#include "utility_name"

void TestFunction()
{
    // Test case 1
    int nResult = MyFunction(5);
    if (nResult != EXPECTED_VALUE)
    {
        WriteTimestampedLogEntry("test.log", "Test 1 FAILED");
    }
    
    // Test case 2
    // ... more tests ...
}

void main()
{
    TestFunction();
    WriteTimestampedLogEntry("test.log", "Tests complete");
}
```

## Documentation Standards

### Function Documentation Template

```nscript
//::///////////////////////////////////////////////////////////////////////////
//:: FunctionName
//::///////////////////////////////////////////////////////////////////////////
//:: Description: Clear explanation of what function does
//:: Parameters:   param1 = description
//::               param2 = description
//:: Returns:      description of return value
//:: Notes:        Any important notes or edge cases
//:: Example:      FunctionName(value1, value2);
//::///////////////////////////////////////////////////////////////////////////
void FunctionName(type param1, type param2)
{
    // Implementation
}
```

## Performance Tips

1. **Avoid string concatenation in loops**
   - Use arrays or accumulator instead
   - Concatenate once after loop

2. **Cache frequently used values**
   - Store GetLocation() result
   - Cache object property queries
   - Reuse calculated values

3. **Use efficient data structures**
   - Choose right container for task
   - Avoid nested loops where possible
   - Pre-sort data if needed multiple times

4. **Minimize function calls**
   - Combine related operations
   - Use local variables for temporary data
   - Reduce parameter passing

## Compatibility

✓ NWN:EE (all versions)  
✓ Standard NWScript  
✓ Aurora Toolset  
✓ All custom systems  
✓ Third-party scripts  

## License

Utility scripts are free to use, modify, and distribute.

**Attribution:** Not strictly required but appreciated  
**License Type:** Open source  
**Modification:** Allowed and encouraged  

## Resources

### NWScript Documentation
- [BioWare NWScript Guide](https://neverwintervaults.org)
- [NWN:EE Official Docs](https://docs.neverwintervault.org)

### External Resources
- [Neverwinter Vault](https://neverwintervault.org)
- [NWN Lexicon](https://nwnlexicon.com)
- [Community Forums](https://neverwintervault.org)

## Support

### Getting Help

1. **Review function documentation** - Most issues covered
2. **Check examples** - Usage patterns shown
3. **Search community** - Others may have solved it
4. **Ask questions** - Create issue with details

### Reporting Issues

When reporting a problem:
1. Describe what you're trying to do
2. Show your code
3. Include error message
4. Describe expected vs actual behavior
5. Provide NWN:EE version

## Summary

Utility scripts provide:
- Common patterns for reuse
- Helper functions to save time
- Best practices implementation
- Foundation for larger systems
- Educational code examples

Use individually or combine to build complex systems efficiently.

---

**What These Scripts Are:**
- Utility functions and helpers
- Common patterns and examples
- Reusable components
- Supporting code for larger systems

**What These Scripts Are NOT:**
- Complete systems (see NUI, CPPS, CT, Commoner repos)
- Game mechanics (those are project-specific)
- Art or asset code
- External dependencies

**Status:** Community-maintained utility collection  
**Quality:** Production-ready where used  
**Testing:** User responsibility  
**Support:** Community-driven

---

**Last Updated:** June 4, 2026  
**Carcerian NWN:EE Scripts - Utilities Section**
