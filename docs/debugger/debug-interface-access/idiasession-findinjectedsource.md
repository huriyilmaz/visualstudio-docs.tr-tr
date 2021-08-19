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
ms.openlocfilehash: 4e7e6aeec300aaf8941fa0d3ac28ddce7ace8de4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044313"
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
