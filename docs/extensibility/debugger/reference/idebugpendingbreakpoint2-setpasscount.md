---
description: Bekleyen kesme noktasıyla ilişkili geçiş sayısını ayarlar veya değiştirir.
title: IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d1d72cc83d66bc0bd553db9ef392bb62d22c3af
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050864"
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
[in] Geçiş [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) içeren bir yapıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Kesme `E_BP_DELETED` noktası silinmişse döndürür.

## <a name="remarks"></a>Açıklamalar
 Daha önce bekleyen kesme noktasıyla ilişkili tüm geçiş sayısı kaybedilir. Bu bekleyen kesme noktasıyla ilişkili tüm kesme noktaları, geçiş sayısını parametresine ayarlamak için `bpPassCount` çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
