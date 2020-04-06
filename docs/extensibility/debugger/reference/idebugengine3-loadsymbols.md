---
title: IDebugEngine3::LoadSymbols | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7963d39601a0d3a90ca2daa7632902d7aa506de8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730804"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Bu hata ayıklama motoru tarafından debugged tüm modüller için yükler (gerektiği gibi) semboller.

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
 Başarılı olursa, S_OK döndürür; aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu, bu hata ayıklama motoru tarafından başvurulan tüm modüller için hata ayıklama sembolleri yükler. Semboller yalnızca zaten yüklenmemişse yüklenir. Semboller [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)için bir çağrı tarafından ayarlanan yollarda aranır.

## <a name="see-also"></a>Ayrıca bkz.
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
