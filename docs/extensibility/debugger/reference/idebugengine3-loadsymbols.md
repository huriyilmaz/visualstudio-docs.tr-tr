---
description: Bu hata ayıklama altyapısı tarafından hata ayıklaması yapılan tüm modüller için gerekli ()) simgeleri yükler.
title: IDebugEngine3::LoadSymbols | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b1faedbca01e1e37ef50894526a7c775205ea215
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111105"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Bu hata ayıklama altyapısı tarafından hata ayıklaması yapılan tüm modüller için gerekli ()) simgeleri yükler.

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
 Başarılı olursa, S_OK; aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu, bu hata ayıklama altyapısı tarafından başvurulan tüm modüller için hata ayıklama sembollerini yükler. Semboller yalnızca henüz yüklenmemişse yüklenir. Semboller, [SetSymbolPath çağrısıyla ayarlanmış yollarda aranır.](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)

## <a name="see-also"></a>Ayrıca bkz.
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
