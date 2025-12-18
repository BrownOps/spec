# BrownOps Message Specification

The official specification for tracking bowel movements via WhatsApp messages.

## Quick Reference

| Command | Example | Description |
|---------|---------|-------------|
| Log event | `💩` | Log right now |
| Log with time | `💩 14:30` | Log at specific time today |
| Log past event | `💩 2025-01-15 14:30` | Log at exact date/time |
| Set timezone | `🚽 +2` | Set offset to +2 hours |
| Set timezone | `🚽 Europe/Rome` | Set by timezone name |

## Events (💩)

### Live Events

```
💩                    # Log now with current timezone
💩 14:30              # Log at 14:30 today
💩 +2                 # Log now with +2 hour offset
💩 Europe/Rome        # Log now in Rome timezone
```

### Past Events

```
💩 2025-01-15 14:30           # Log at exact time (no shift applied)
💩 +2 2025-01-15 14:30        # Log at 14:30, store +2 for reference
💩 Europe/Rome 2025-01-15 14:30   # Log at 14:30, store timezone for reference
```

> **Note**: When logging past events with a date/time, any shift or timezone is stored for statistics only — it doesn't modify the timestamp.

## Settings (🚽)

### Timezone Offset

```
🚽 +2                 # Set +2 hours from UTC
🚽 -5                 # Set -5 hours from UTC
🚽 +5:30              # Set +5.5 hours (fractional)
🚽 0                  # Reset to UTC
```

### Named Timezones

```
🚽 Europe/Rome        # Set to Rome timezone
🚽 America/New_York   # Set to New York timezone
🚽 PST                # Set to Pacific Standard Time
🚽 UTC                # Set to UTC
```

### Retroactive Settings

```
🚽 +2 2025-01-15 09:00    # Set +2 effective from Jan 15, 09:00
```

Use this when you forgot to update your timezone and want past events recalculated.

## Metadata

Add context with extra emojis between the command and time/shift:

```
💩 🩸                     # Flag with metadata
💩 🧱                     # Note consistency
💩 ☕ 🍕                  # Track what you consumed
💩 🩸 +2                  # Metadata + shift
💩 🧱 14:30               # Metadata + time
💩 🩸💧 2025-01-15 14:30  # Metadata + past event
🚽 ✈️ +8                  # Setting with travel context
```

Metadata emojis are stored with the event for later analysis.

## Date/Time Formats

Supported formats for specifying times:

```
2025-01-15 14:30          # Date + time (recommended)
2025-01-15 14:30:00       # With seconds
2025/01/15 14:30          # Slash separator
14:30                     # Time only (today)
```

## Implementations

- **Ruby**: [toilet_tracker](https://github.com/BrownOps/toilet_tracker)
- **Python**: [loo_parser.py](https://github.com/BrownOps/loo_parser.py) *(coming soon)*

## Version

Specification v2.0 — December 2025
