---
name: agent-tool-builder
description: "Guides students through authoring and validating custom @tool functions and MCP endpoints."
---

# Agent Tool Builder

## Overview
The `agent-tool-builder` skill instructs learners on crafting robust, self-describing Python tools compatible with `smolagents` and the Model Context Protocol (MCP).

## Tool Design Principles
1. **Clear Semantic Docstrings:** LLM agents depend entirely on the function docstring and argument descriptions to decide when and how to call a tool.
2. **Strict Type Annotations:** Annotate all parameters (`str`, `int`, `float`, `list[str]`, etc.) and return values.
3. **Graceful Error Handling:** Wrap tool operations in `try/except` blocks that return informative error strings rather than crashing the agent process.

## Decorator Pattern
```python
from smolagents import tool

@tool
def calculate_travel_time(distance_km: float, speed_kmh: float) -> float:
    """Calculates travel time in hours given distance and speed.
    
    Args:
        distance_km: The distance to travel in kilometers.
        speed_kmh: The average travel speed in kilometers per hour.
    """
    if speed_kmh <= 0:
        return -1.0
    return distance_km / speed_kmh
```
