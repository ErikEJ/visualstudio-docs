---
description: "This method sets the language that the process will be hosted under."
title: IDebugProcess3::SetHostingProcessLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: maiak
ms.author: maiak
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
---
# IDebugProcess3::SetHostingProcessLanguage

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
This method sets the language that the process will be hosted under. This language can then be used by the debug engine (DE) to load the appropriate expression evaluator.

## Syntax

### [C#](#tab/csharp)
```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```
### [C++](#tab/cpp)
```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```
---

## Parameters
`guidLang`\
[in] `GUID` of the language that the DE should use. Specify `GUID_NULL` (C++) or `Guid.Empty` (C#) to have the DE use the default language.

## Return Value
 If successful, returns `S_OK`; otherwise, returns error code.

## Remarks
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) can be used to retrieve the current language setting.

## See also
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
