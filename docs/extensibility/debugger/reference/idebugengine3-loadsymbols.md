---
description: Bu hata ayıklama altyapısı tarafından hata ayıklamakta olan tüm modüller için (gerektiğinde) semboller yükler.
title: 'IDebugEngine3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43651baac29b3904b9bc12d8d4b965ca1cd8e3ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066196"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Bu hata ayıklama altyapısı tarafından hata ayıklamakta olan tüm modüller için (gerektiğinde) semboller yükler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu hata ayıklama altyapısı tarafından başvurulan tüm modüller için hata ayıklama sembolleri yükler. Semboller yalnızca henüz yüklenmediyse yüklenir. Simgeler [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)çağrısıyla ayarlanan yollarda aranır.

## <a name="see-also"></a>Ayrıca bkz.
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
