---
description: Bu bekleyen kesme noktasından bağlantılı olan tüm kesme noktalarını numaralandırır.
title: 'IDebugPendingBreakpoint2:: EnumBoundBreakpoints | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::EnumBoundBreakpoints
helpviewer_keywords:
- EnumBoundBreakpoints method
- IDebugPendingBreakpoint2::EnumBoundBreakpoints method
ms.assetid: 179c7c54-8446-462d-b099-e0f9cf06dc52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf5715983a64ea361f60978251981b1ea7325c0cec9f815f7d28a1f2a725df27
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121339222"
---
# <a name="idebugpendingbreakpoint2enumboundbreakpoints"></a>IDebugPendingBreakpoint2::EnumBoundBreakpoints
Bu bekleyen kesme noktasından bağlantılı olan tüm kesme noktalarını numaralandırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumBoundBreakpoints( 
   IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
   out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
dışı , Bağlantılı kesme noktalarını numaralandırır bir [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_BP_DELETED`Kesme noktasının silinip silinmediğini döndürür.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `CPendingBreakpoint` [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimini kullanıma sunan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CPendingBreakpoint::EnumBoundBreakpoints(IEnumDebugBoundBreakpoints2** ppEnum)
{
   HRESULT hr;

   // Verify that the passed IEnumDebugBoundBreakpoints2 interface pointer
   // is valid.
   if (ppEnum)
   {
      *ppEnum = NULL;

      // Verify that the pending breakpoint has not been deleted. If
      // deleted, then return hr = E_BP_DELETED.
      if (m_state.state != PBPS_DELETED)
      {
         // If the bound breakpoint member variable is valid.
         if (m_pBoundBP)
         {
            // Get the bound breakpoint.
            CComPtr<IDebugBoundBreakpoint2> spBoundBP;
            hr = m_pBoundBP->QueryInterface(&spBoundBP);
            assert(hr == S_OK);
            if (hr == S_OK)
            {
               // Create the bound breakpoint enumerator.
               CComObject<CEnumDebugBoundBreakpoints>* pBoundEnum;
               hr = CComObject<CEnumDebugBoundBreakpoints>::CreateInstance(&pBoundEnum);
               assert(hr == S_OK);
               if (hr == S_OK)
               {
                  // Initialize the enumerator of bound breakpoints with
                  // the IDebugBoundBreakpoint2 information.
                  IDebugBoundBreakpoint2* rgBoundBP[] = { spBoundBP.p };
                  hr = pBoundEnum->Init(rgBoundBP, &(rgBoundBP[1]), NULL, AtlFlagCopy);
                  if (hr == S_OK)
                  {
                     // Verify that the passed IEnumDebugBoundBreakpoints2
                     // interface can be queried by the created
                     // CEnumDebugBoundBreakpoints object.
                     hr = pBoundEnum->QueryInterface(ppEnum);
                     assert(hr == S_OK);
                  }

                  // Otherwise, delete the CEnumDebugBoundBreakpoints object.
                  if (FAILED(hr))
                  {
                     delete pBoundEnum;
                  }
               }
            }
         }
         else
         {
            hr = S_FALSE;
         }
      }
      else
      {
         hr = E_BP_DELETED;
      }
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
