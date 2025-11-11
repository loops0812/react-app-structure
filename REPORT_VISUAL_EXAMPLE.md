# JasperReports STB Grouping - Visual Example

## How the Report Would Look

Based on the sample data, here's how the report would render:

### Title Section
```
                    LIỆT KÊ CHỨNG TỪ - BẢNG SỐ
```

### Group 1: STB001 (STT = 1)
```
┌─────┬────────┬──────────────────────┬────────────────────────┬──────────────┬─────────────────┐
│ STT │  STB   │    Tên Khách Hàng    │        Địa Chỉ         │   Số Tiền    │  Ngày Chứng Từ  │
├─────┼────────┼──────────────────────┼────────────────────────┼──────────────┼─────────────────┤
│  1  │ STB001 │                      │                        │              │                 │
├─────┼────────┼──────────────────────┼────────────────────────┼──────────────┼─────────────────┤
│     │        │ Nguyen Van A         │ 123 Le Loi, TP.HCM     │  1,000,000.00│    15/09/2025   │
├─────┼────────┼──────────────────────┼────────────────────────┼──────────────┼─────────────────┤
│     │        │ Tran Thi B           │ 456 Nguyen Hue, TP.HCM │  2,000,000.00│    15/09/2025   │
├─────┼────────┼──────────────────────┼────────────────────────┼──────────────┼─────────────────┤
│     │        │ Le Van C             │ 789 Dong Khoi, TP.HCM  │  1,500,000.00│    15/09/2025   │
└─────┴────────┴──────────────────────┴────────────────────────┴──────────────┴─────────────────┘
```

### Group 2: STB002 (STT = 2)
```
┌─────┬────────┬──────────────────────┬────────────────────────┬──────────────┬─────────────────┐
│  2  │ STB002 │                      │                        │              │                 │
├─────┼────────┼──────────────────────┼────────────────────────┼──────────────┼─────────────────┤
│     │        │ Pham Thi D           │ 321 Hai Ba Trung, HN   │  3,000,000.00│    16/09/2025   │
├─────┼────────┼──────────────────────┼────────────────────────┼──────────────┼─────────────────┤
│     │        │ Hoang Van E          │ 654 Hoan Kiem, Ha Noi  │  2,500,000.00│    16/09/2025   │
└─────┴────────┴──────────────────────┴────────────────────────┴──────────────┴─────────────────┘
```

### Group 3: STB003 (STT = 3)
```
┌─────┬────────┬──────────────────────┬────────────────────────┬──────────────┬─────────────────┐
│  3  │ STB003 │                      │                        │              │                 │
├─────┼────────┼──────────────────────┼────────────────────────┼──────────────┼─────────────────┤
│     │        │ Vu Thi F             │ 987 Bach Mai, Ha Noi   │  1,800,000.00│    17/09/2025   │
└─────┴────────┴──────────────────────┴────────────────────────┴──────────────┴─────────────────┘
```

### Summary Section
```
┌─────────────────────────────────────────────────────────────────────────────┬──────────────┐
│                                                              Tổng cộng:     │ 11,800,000.00│
└─────────────────────────────────────────────────────────────────────────────┴──────────────┘
```

### Footer
```
                                                                    Trang 1 / 1
```

## Key Features Demonstrated

1. **Merged STB Cells**: Notice how STB001, STB002, STB003 appear only once per group
2. **Group-based STT**: STT increments by group (1, 2, 3) not by individual rows
3. **Visual Grouping**: Gray background headers separate each STB group
4. **Proper Alignment**: 
   - STT and STB centered
   - Customer names and addresses left-aligned
   - Amounts right-aligned with currency formatting
   - Dates center-aligned with DD/MM/YYYY format
5. **Summary**: Total amount calculated across all groups

## Before vs After

### Before (Problem State)
- STT would be: 1, 2, 3, 4, 5, 6 (per row)
- STB would repeat: STB001, STB001, STB001, STB002, STB002, STB003
- Casting errors on STT field
- No visual grouping

### After (Solution Implemented)
- STT is: 1, 2, 3 (per group)
- STB appears once per group with merged cells
- Proper Integer type handling for STT
- Clear visual grouping with headers