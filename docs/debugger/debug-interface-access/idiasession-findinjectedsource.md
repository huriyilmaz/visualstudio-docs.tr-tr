---
description: Öznitelik sağlayıcıları veya derleme işleminin diğer bileşenleri tarafından sembol deposuna yerleştirilmiş kaynakların listesini alın.
title: IDiaSession::findInjectedSource | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3c26a677b826ec706934bb75024b5aa956a9709c8715b97afd1dc0a608c3c283
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391843"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Öznitelik sağlayıcıları veya derleme işleminin diğer bileşenleri tarafından sembol deposuna yerleştirilmiş kaynakların listesini alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 srcFile

[in] Aranır kaynak dosyanın adı.

 ppResult

[out] Tüm [eklenir kaynakların listesini içeren bir IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
