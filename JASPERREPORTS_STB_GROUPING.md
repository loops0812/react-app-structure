# JasperReports STB Grouping Implementation

## Overview
This document explains the implementation of STB grouping functionality in the JasperReports file `LIETKECHUNGTU_BS_15092025-1.jrxml`.

## Problem Solved

### 1. STB Cell Merging
- **Issue**: Cells with same STB values were not merged
- **Solution**: Implemented `GroupStb` group with `groupExpression="$F{stb}"` that automatically merges cells with the same STB value

### 2. STT Numbering by Group
- **Issue**: STT was incrementing by row instead of by STB group
- **Solution**: Created `groupSTT` variable with `resetType="Group"` and `resetGroup="GroupStb"` that resets and increments for each STB group

### 3. Casting Error Fix
- **Issue**: "java.lang.String cannot be cast to class java.lang.Number" error
- **Solution**: 
  - Defined `groupSTT` variable as `java.lang.Integer` class
  - Used proper data types for all fields (String, BigDecimal, Date)
  - Added null checks and default values

## Technical Implementation

### Group Definition
```xml
<group name="GroupStb" isStartNewPage="false" isResetPageNumber="false">
    <groupExpression><![CDATA[$F{stb}]]></groupExpression>
    <!-- Group header and footer bands -->
</group>
```

### STT Variable
```xml
<variable name="groupSTT" class="java.lang.Integer" resetType="Group" resetGroup="GroupStb" calculation="Count">
    <variableExpression><![CDATA[1]]></variableExpression>
    <initialValueExpression><![CDATA[0]]></initialValueExpression>
</variable>
```

### Group Header
- Displays STT (group number) and STB value
- Uses `isPrintRepeatedValues="false"` to prevent repetition
- Provides column headers for the detail data

### Detail Band
- Contains only the data fields (not STT and STB)
- STT and STB columns are left empty in detail band (merged with group header)
- Includes proper null checking and formatting

## Features

### 1. Automatic Grouping
- Rows with the same STB value are automatically grouped together
- Group header shows the STT and STB for the entire group
- Detail rows within the group show other field data

### 2. Proper Data Types
- **STB**: `java.lang.String`
- **STT (groupSTT)**: `java.lang.Integer`
- **soTien**: `java.math.BigDecimal` with number formatting
- **ngayChungTu**: `java.sql.Date` with date formatting

### 3. Visual Layout
- Group headers have gray background for clear separation
- Borders around all cells for clear structure
- Proper alignment (center for numbers, left for text, right for amounts)
- Page numbering and summary totals

### 4. Data Safety
- Null checks on all field expressions
- Default values for empty fields
- Proper exception handling for type conversions

## Usage

1. The report expects data with fields: `stb`, `tenKhachHang`, `diaChi`, `soTien`, `ngayChungTu`
2. Data will be automatically grouped by STB value
3. STT will increment by group (1, 2, 3, etc.) not by row
4. Each group will have merged STB cells
5. Summary section shows total amount

## Result
- ✅ STB cells are merged for same values
- ✅ STT increments by group, not by row
- ✅ No more casting errors
- ✅ Clean, organized report layout
- ✅ Proper data type handling