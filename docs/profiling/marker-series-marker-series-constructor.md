---
description: Marker_series sınıfının yeni bir örneğini başlatır.
title: 'marker_series:: marker_series Oluşturucu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 16e766bc5c22cc6c9efb257c22326a4addf4bf0f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076470"
---
# <a name="marker_seriesmarker_series-constructor"></a>marker_series:: marker_series Oluşturucusu
`marker_series` sınıfının yeni bir örneğini başlatır.

## <a name="syntax"></a>Sözdizimi

```cpp
marker_series();
marker_series(
   _In_ LPCTSTR _SeriesName
);
marker_series(
   _In_ const GUID* _ProviderGuid
);
marker_series(
   _In_ const GUID* _ProviderGuid,
   _In_ LPCTSTR _SeriesName
);
```

#### <a name="parameters"></a>Parametreler
 `_SeriesName` Oluşturulacak serinin adı.

 `_ProviderGuid` Seri sağlayıcının GUID 'SI.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj. h*

 **Ad alanı:** Eşzamanlılık::d ıagstik

## <a name="see-also"></a>Ayrıca bkz.
- [marker_series sınıfı](../profiling/marker-series-class.md)
