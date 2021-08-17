---
description: Yüklenen veya kaldırılan modülü alır.
title: IDebugModuleLoadEvent2::GetModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c632f0de62f931b68b56c321e846eca9265f50b9c19f0704da7fee2b7bd8a8ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417047"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Yüklenen veya kaldırılan modülü alır.

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
[out] Yükleniyor veya kaldırılan modülü temsil eden bir [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) nesnesi döndürür.

`pbstrDebugMessage`\
[in, out] Bu olayı açıklayan isteğe bağlı bir ileti döndürür. Bu parametre null bir değerse ileti isteğinde yoktur.

`pbLoad`\
[in, out] Modül yükleniyorsa sıfır ( ) ve modül `TRUE` kaldırıyorsa sıfır ( ) olarak `FALSE` ayarlayın. Bu parametre null bir değerse durum isteği yoktur.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
