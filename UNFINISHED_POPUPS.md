# Unfinished Popups Inventory

Complete status of all NUI popup functions - what's done, what's not, and what's needed.

**Last Updated:** June 4, 2026 | **Total Popups:** 65+ | **Complete:** 5 | **Unfinished:** 60+

---

## Status Legend

- ✅ **COMPLETE** - Fully implemented, tested, documented
- 🟡 **PARTIAL** - Partially implemented, needs work
- 🔴 **NOT_STARTED** - Planned but not implemented
- 🔵 **NEEDS_TESTING** - Implemented but untested in-game
- ⚠️ **BLOCKED** - Waiting on something else
- 🚧 **IN_PROGRESS** - Currently being worked on

---

## Standard Message Popups

### Core Message Functions

| Status | Function | Parameters | Returns | Needs |
|--------|----------|-----------|---------|-------|
| ✅ | NUI_PopupMessage | (oPC, sTitle, sMessage[, fX, fY, fWidth, fHeight, sScript]) | int | - |
| ✅ | NUI_PopupError | (oPC, sTitle, sMessage) | int | - |
| ✅ | NUI_PopupSuccess | (oPC, sTitle, sMessage) | int | - |
| ✅ | NUI_PopupWarning | (oPC, sTitle, sMessage) | int | - |
| ✅ | NUI_PopupInfo | (oPC, sTitle, sMessage) | int | - |

**Status:** All basic messages complete ✅

---

## Interactive Choice Popups

### Yes/No & Choice Functions

| Status | Function | Use Case | Needs |
|--------|----------|----------|-------|
| 🔴 | NUI_PopupYesNo | Simple yes/no decision | Event handling, response routing |
| 🔴 | NUI_PopupChoice | Multiple option selection | Choice storage, response parsing |
| 🔴 | NUI_PopupConfirm | Confirmation before action | Event integration |
| 🔴 | NUI_PopupInput | Text input from player | Text validation, input storage |

**Priority:** HIGH - Core functionality needed

**Requirements for All:**
- [ ] Event handling for button clicks
- [ ] Storage of player choice
- [ ] Response callback system
- [ ] Timeout handling (auto-close after X seconds)
- [ ] Cancel button implementation

---

## Specialized Display Popups

### Sign & Display Functions

| Status | Function | Current State | Needs |
|--------|----------|---------------|-------|
| ✅ | NUI_PopupSign | Fully working with portrait XML layout | - |
| 🔴 | NUI_PopupBook | Book/journal display | Multi-page support, page turning |
| 🔴 | NUI_PopupScroll | Ancient scroll display | Parchment texture, aging effect |
| 🔴 | NUI_PopupGrimoire | Spellbook display | Spell listing, category sorting |
| 🔴 | NUI_PopupMap | Map/minimap display | Location markers, zoom controls |
| 🔴 | NUI_PopupPortrait | Character portrait gallery | Image navigation, filtering |

**Priority:** MEDIUM - Visual presentation

**Common Requirements:**
- [ ] Multi-page navigation
- [ ] Image asset handling
- [ ] Scrolling content support
- [ ] Zoom/scale controls
- [ ] Search/filter support (where applicable)

---

## Inventory & Item Popups

### Item Management Functions

| Status | Function | Purpose | Needs |
|--------|----------|---------|-------|
| 🔴 | NUI_PopupInventory | Display player inventory | Item listing, filtering, sorting |
| 🔴 | NUI_PopupItemSelect | Select item from inventory | Item validation, type checking |
| 🔴 | NUI_PopupShop | Merchant shop display | Buy/sell prices, quantity control |
| 🔴 | NUI_PopupLoot | Loot distribution window | Quantity selection, confirmation |
| 🔴 | NUI_PopupCraft | Crafting recipe selection | Recipe listing, ingredient display |
| 🔴 | NUI_PopupEnchant | Enchantment application | Effect preview, cost display |

**Priority:** HIGH - Player interaction critical

**Core Requirements for Inventory Functions:**
- [ ] Item filtering by type
- [ ] Item property display (weight, value, AC, etc.)
- [ ] Sorting options (name, value, weight, type)
- [ ] Search functionality
- [ ] Selection/multi-selection
- [ ] Pagination for large inventories
- [ ] Item descriptions on hover

---

## Character Customization Popups

### Appearance & Stats Functions

| Status | Function | Purpose | Needs |
|--------|----------|---------|-------|
| 🔴 | NUI_PopupAppearance | Full appearance customizer | Body part selection UI |
| 🔴 | NUI_PopupColorPicker | RGB color selection | Color picker widget, RGB sliders |
| 🔴 | NUI_PopupStatAllocation | Ability score allocation | Point display, +/- buttons |
| 🔴 | NUI_PopupSkillSelect | Skill selection/management | Skill listing, point allocation |
| 🔴 | NUI_PopupFeatSelect | Feat selection/management | Feat listing, prerequisites check |
| 🔴 | NUI_PopupClass | Class selection/information | Class descriptions, requirements |

**Priority:** HIGH - Core character development

**Color Picker Specific:**
- [ ] RGB input fields (0-255 each)
- [ ] Hex input field
- [ ] Color preview swatch
- [ ] Named color palette
- [ ] Recent colors history

**Stat/Skill/Feat Pickers Specific:**
- [ ] Point allocation display
- [ ] +/- buttons for adjustments
- [ ] Prerequisite checking
- [ ] Min/max enforcement
- [ ] Summary display

---

## Combat & Status Popups

### Combat & Information Functions

| Status | Function | Purpose | Needs |
|--------|----------|---------|-------|
| 🔴 | NUI_PopupCombatLog | Combat action logging | Scrolling text display |
| 🔴 | NUI_PopupBuffs | Active buffs/debuffs display | Duration tracking, icon display |
| 🔴 | NUI_PopupCharacterSheet | Full character sheet | Multi-tab layout, stat grouping |
| 🔴 | NUI_PopupPartyStatus | Party member status | Health bars, status effects |
| 🔴 | NUI_PopupSpellInfo | Spell information display | DC, range, description, components |
| 🔴 | NUI_PopupTargetInfo | Selected target information | Health, faction, attitude |

**Priority:** MEDIUM - Quality of life

**Requirements:**
- [ ] Real-time updates for status
- [ ] Dynamic content refresh
- [ ] Color coding for buffs/debuffs
- [ ] Icon/image support
- [ ] Duration countdown display

---

## Dialog & Conversation Popups

### Interactive Dialog Functions

| Status | Function | Purpose | Needs |
|--------|----------|---------|-------|
| ✅ | NUI_DialogCreate | Custom dialog with flexible content | - |
| 🔴 | NUI_PopupConversation | NPC conversation display | Reply selection, speaker identification |
| 🔴 | NUI_PopupQuest | Quest display & objectives | Objective tracking, map markers |
| 🔴 | NUI_PopupBarter | Barter/trade window | Two-way item exchange |
| 🔴 | NUI_PopupDialog | Multi-option dialog | Button generation from array |

**Priority:** HIGH - Player interaction

**Requirements:**
- [ ] Option button generation from array
- [ ] Speaker name display
- [ ] Portrait display for speaker
- [ ] Dialog history (previous exchanges)
- [ ] Response validation

---

## Search & Filter Popups

### Utility & Browser Functions

| Status | Function | Purpose | Needs |
|--------|----------|---------|-------|
| 🔴 | NUI_PopupSearch | Search/filter interface | Search box, filter options, results |
| 🔴 | NUI_PopupBrowser | Generic item/content browser | Pagination, sorting, filtering |
| 🔴 | NUI_PopupList | Scrolling list selection | Dynamic list building, selection |
| 🔴 | NUI_PopupTable | Table/grid display | Row/column layout, sorting |
| 🔴 | NUI_PopupDropdown | Dropdown selection | Expandable list, collapsing |

**Priority:** MEDIUM - Content organization

**Requirements:**
- [ ] Pagination support
- [ ] Search text matching
- [ ] Filter criteria support
- [ ] Sorting options
- [ ] Selection tracking

---

## Advanced Features

### Complex Popup Functions

| Status | Function | Purpose | Complexity | Needs |
|--------|----------|---------|-----------|-------|
| 🔴 | NUI_PopupSlider | Slider control for value selection | Medium | Min/max enforcement, real-time feedback |
| 🔴 | NUI_PopupProgress | Progress bar display | Low | Percentage calculation, dynamic update |
| 🔴 | NUI_PopupLoading | Loading screen/spinner | Low | Animation simulation |
| 🔴 | NUI_PopupNotification | Toast notification system | Low | Auto-hide timer |
| 🔴 | NUI_PopupContextMenu | Right-click context menu | Medium | Mouse position tracking, option routing |
| 🔴 | NUI_PopupDragDrop | Drag & drop interface | High | Mouse event handling, item tracking |
| 🔴 | NUI_PopupTabbed | Tabbed interface | Medium | Tab selection, content switching |
| 🔴 | NUI_PopupModal | Modal dialog (blocks background) | Low | Input focus, background dimming |

**Priority:** LOW - Advanced features

**Complexity Notes:**
- Slider: Requires fine input control
- ContextMenu: Requires mouse coordinate detection
- DragDrop: Requires complex event handling
- Tabbed: Good medium complexity starting point

---

## Summary by Implementation Priority

### TIER 1 (Do First - High Value)
**Impact: Critical player interaction**

1. NUI_PopupYesNo (simple, reusable)
2. NUI_PopupInventory (core feature)
3. NUI_PopupItemSelect (core feature)
4. NUI_PopupColorPicker (needed for CT system)
5. NUI_PopupChoice (fundamental)

**Estimated effort:** 40-60 hours
**Impact on other systems:** Very High

---

### TIER 2 (Do Next - Medium Value)
**Impact: Good to have, enhances gameplay**

1. NUI_PopupShop (commerce)
2. NUI_PopupConversation (dialog)
3. NUI_PopupQuest (quest display)
4. NUI_PopupCharacterSheet (info)
5. NUI_PopupAppearance (appearance)

**Estimated effort:** 50-70 hours
**Impact on other systems:** Medium

---

### TIER 3 (Do Later - Enhancement)
**Impact: Quality of life improvements**

1. NUI_PopupBrowser (generic utility)
2. NUI_PopupList (utility)
3. NUI_PopupSearch (utility)
4. NUI_PopupBuffs (status display)
5. NUI_PopupBook (content display)

**Estimated effort:** 30-50 hours
**Impact on other systems:** Low

---

### TIER 4 (Advanced - Nice to Have)
**Impact: Polish & advanced features**

1. NUI_PopupSlider (advanced control)
2. NUI_PopupTabbed (layout improvement)
3. NUI_PopupTable (data display)
4. NUI_PopupContextMenu (advanced interaction)
5. NUI_PopupDragDrop (very advanced)

**Estimated effort:** 60-100 hours (high complexity)
**Impact on other systems:** Low

---

## Dependencies & Blocking Issues

### Blocking Tier 1 Implementation
- ⚠️ **Event handling system** - Needs robust button click routing
- ⚠️ **Input validation** - Needed for choice storage
- ⚠️ **Response callback system** - For action execution

**Status:** Event handling partially done in nui_api_handle.nss ✓

### Blocking Tier 2 Implementation
- ✅ Tier 1 popups (prerequisite)
- ⚠️ NPC conversation system (for NUI_PopupConversation)
- ⚠️ Quest system integration (for NUI_PopupQuest)

**Status:** Some waiting on game systems

---

## Implementation Strategy

### For Each Popup, Create:

1. **Function in nui_api_popup.nss**
   ```nscript
   int NUI_PopupNew(object oPC, [parameters])
   {
       // Build window
       // Create popup
       // Return token
   }
   ```

2. **Event handler in nui_api_handle.nss**
   - Button click routing
   - Response storage
   - Callback execution

3. **Documentation in FUNCTION_INDEX.md**
   - Signature
   - Parameters
   - Return value
   - Include file

4. **Example in utilities or README**
   - Sample usage
   - Common patterns
   - Error handling

---

## Testing Checklist Template

For each new popup:

```
✓ Window appears on screen
✓ Window has correct title
✓ Content displays correctly
✓ All buttons/controls present
✓ Buttons respond to clicks
✓ Window closes when requested
✓ AOE cleanup works (if applicable)
✓ Multiple popups don't conflict
✓ Error conditions handled gracefully
✓ Performance acceptable
```

---

## Quick Stats

| Metric | Count |
|--------|-------|
| Total Popup Functions | 65+ |
| Currently Complete | 5 |
| Partially Complete | 0 |
| Not Started | 60+ |
| Estimated Total Hours | 180-280 |
| Estimated Completion Time | 4-7 weeks (full-time) |

---

## By Category Summary

| Category | Count | Complete | Needed |
|----------|-------|----------|--------|
| Basic Messages | 5 | 5 | 0 |
| Choice/Interactive | 4 | 0 | 4 |
| Display/Visual | 6 | 1 | 5 |
| Inventory/Items | 6 | 0 | 6 |
| Customization | 6 | 0 | 6 |
| Combat/Status | 6 | 0 | 6 |
| Dialog/Conversation | 5 | 1 | 4 |
| Search/Filter | 5 | 0 | 5 |
| Advanced Features | 8 | 0 | 8 |

**Completion Rate:** 8.5% (6 of 65+ complete)

---

## Recommended Next Steps

### Immediate (This Week)
1. Implement NUI_PopupYesNo - Simple, reusable
2. Implement NUI_PopupChoice - Fundamental
3. Add comprehensive event routing

### Short Term (Next 2 Weeks)
1. Implement NUI_PopupColorPicker - Needed for CT
2. Implement NUI_PopupInventory - High impact
3. Implement NUI_PopupItemSelect - High impact

### Medium Term (Weeks 3-4)
1. Implement NUI_PopupShop - Commerce system
2. Implement NUI_PopupConversation - Dialog
3. Implement NUI_PopupQuest - Quest system

### Long Term (Weeks 5+)
1. Implement remaining utility popups
2. Implement advanced features (sliders, tabs, etc.)
3. Polish and optimization

---

## How AI Can Help

**Using this document, AI can:**

1. ✅ See exactly what's needed
2. ✅ Understand priority order
3. ✅ Know dependencies
4. ✅ Follow consistent pattern
5. ✅ Test each popup thoroughly
6. ✅ Document as it goes
7. ✅ Not waste time on wrong implementations

**Result:** Faster, more focused development

---

**Last Updated:** June 4, 2026  
**Maintained by:** Carcerian  
**Status:** Active Development Plan
