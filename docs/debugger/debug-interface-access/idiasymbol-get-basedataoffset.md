---
description: "Retrieves the base data offset."
title: "IDiaSymbol::get_baseDataOffset | Microsoft Docs"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
ms.assetid: bb2ff5ed-9293-4c37-9741-654058b571c5
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
  - "multiple"
---
# IDiaSymbol::get_baseDataOffset

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the base data offset.

## Syntax

```C++
HRESULT get_baseDataOffset(
   DWORD* pRetVal);
```

#### Parameters
 `pRetVal`

[out] A pointer to a `DWORD` that holds the base data offset.

## Return Value
 If successful, returns `S_OK`; otherwise, returns `S_FALSE` or an error code.

## See also
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
