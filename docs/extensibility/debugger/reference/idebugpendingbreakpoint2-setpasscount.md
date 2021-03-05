---
description: Bekleyen kesme noktasıyla ilişkili geçiş sayısını ayarlar veya değiştirir.
title: 'IDebugPendingBreakpoint2:: SetPassCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69d12eb069342e77d92f4b551750c11ccb684dbd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169775"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Bekleyen kesme noktasıyla ilişkili geçiş sayısını ayarlar veya değiştirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parametreler
`bpPassCount`\
'ndaki Geçiş sayısını içeren [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_BP_DELETED`Kesme noktasının silinip silinmediğini döndürür.

## <a name="remarks"></a>Açıklamalar
 Daha önce bekleyen kesme noktasıyla ilişkili olan tüm geçiş sayısı kaybolur. Bu bekleyen kesme noktasından bağlantılı tüm kesme noktaları, geçiş sayısını parametreye ayarlamak için çağırılır `bpPassCount` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
