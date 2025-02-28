---
description: "Retrieves the application entry point."
title: IDebugComPlusSymbolProvider::GetEntryPoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetEntryPoint
- GetEntryPoint
ms.assetid: 9640e121-1da1-41f9-8e66-76efca36baf2
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
# IDebugComPlusSymbolProvider::GetEntryPoint

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the application entry point.

## Syntax

### [C#](#tab/csharp)
```csharp
int GetEntryPoint(
    uint              ulAppDomainID,
    Guid              guidModule,
    out IDebugAddress ppAddress
);
```
### [C++](#tab/cpp)
```cpp
HRESULT GetEntryPoint(
    ULONG32         ulAppDomainID,
    GUID            guidModule,
    IDebugAddress** ppAddress
);
```
---

## Parameters
`ulAppDomainID`\
[in] Identifier for the application domain.

`guidModule`\
[in] Unique identifier for the module.

`ppAddress`\
[out] Returns the entry point represented by an [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

## Return Value
If successful, returns `S_OK`; otherwise, returns an error code.

## Example
The following example shows how to implement this method for a **CDebugSymbolProvider** object that exposes the [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.

```cpp
HRESULT CDebugSymbolProvider::GetEntryPoint(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IDebugAddress **ppAddress
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppAddress, IDebugAddress *));

    METHOD_ENTRY( CDebugSymbolProvider::GetEntryPoint );

    IfFalseGo( ppAddress, E_INVALIDARG );

    *ppAddress = NULL;

    IfFailGo( GetModule( idModule, &pModule) );

    IfFailGo( pModule->GetEntryPoint( ppAddress ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetEntryPoint, hr );

    return hr;
}
```

## See also
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
