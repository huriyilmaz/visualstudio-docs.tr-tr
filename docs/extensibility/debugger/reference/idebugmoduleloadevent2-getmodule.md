---
title: IDebugModuleLoadEvent2::GetModule | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b90547709e5524ce005b0598b0b8d482cfecf173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726728"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Yüklenen veya boşaltılan modülü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Parametreler
`pModule`\
[çıkış] Yükleniyor veya boşaltan modülü temsil eden bir [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) nesnesi döndürür.

`pbstrDebugMessage`\
[içinde, dışarı] Bu olayı açıklayan isteğe bağlı bir ileti döndürür. Bu parametre null değeri ise, ileti istenmez.

`pbLoad`\
[içinde, dışarı] Sıfırsız`TRUE`( ) modül yükleniyorsa ve sıfır (`FALSE`) modül boşaltıyorsa. Bu parametre null değeri ise, durum istenmez.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
