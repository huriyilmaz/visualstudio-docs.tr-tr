---
description: Yüklenmekte olan veya bellekten kaldırılan modülü alır.
title: 'IDebugModuleLoadEvent2:: GetModule | Microsoft Docs'
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
ms.openlocfilehash: d2bca5417403df2479d5de22aeaef4480feb9331
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126979"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Yüklenmekte olan veya bellekten kaldırılan modülü alır.

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
dışı Yükleme veya kaldırma işlemi olan modülü temsil eden bir [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) nesnesi döndürür.

`pbstrDebugMessage`\
[in, out] Bu olayı açıklayan isteğe bağlı bir ileti döndürür. Bu parametre null bir değer ise, herhangi bir ileti istenmez.

`pbLoad`\
[in, out] Modül `TRUE` yüklüyorsanız sıfır ( `FALSE` ) ve modül boşaltılıyor. Bu parametre null bir değer ise, herhangi bir durum istenmez.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
