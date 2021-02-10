---
title: StartTrackingContextWithRoot | Microsoft Docs
description: Bir kök işaretleyici belirten yanıt dosyası kullanarak bir izleme bağlamını başlatmak için MSBuild StartTrackingContextWithRoot kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b52541c99fa81f31eddde8e6c12ad2eee04f3c20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967052"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Bir kök işaretleyici belirten yanıt dosyası kullanarak izleme bağlamını başlatır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametreler

'ndaki `intermediateDirectory`

 İzleme günlüğünün depolayabileceği dizin.

'ndaki `taskName`

 İzleme bağlamını tanımlar. Bu ad, günlük dosyası adını oluşturmak için kullanılır.

'ndaki `rootMarkerResponseFile`

 Kök işaretleyici içeren bir yanıt dosyasının yol adı. Kök adı bir bağlam için tüm izlemeyi gruplamak üzere kullanılır.

## <a name="return-value"></a>Döndürülen değer

 İzleme bağlamı oluşturulduysa, **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [StartTrackingContext](../msbuild/starttrackingcontext.md)