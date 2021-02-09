---
title: 'IDiaSession:: Finınjectedsource | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a49af12ed317732271d755477a2f50e6bb424205
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855223"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Öznitelik sağlayıcıları veya derleme sürecinin diğer bileşenleri tarafından sembol deposuna yerleştirilmiş kaynakların listesini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 Trgblob

'ndaki Aranacak kaynak dosyanın adı.

 ppResult

dışı Tüm eklenen kaynakların bir listesini içeren bir [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)