---
title: StartTrackingContextWithRoot | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36b48529f82a908ea765151561a71c58cd2c7bc5
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578426"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
Bir kök işaretleyici belirten yanıt dosyası kullanarak izleme bağlamını başlatır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametreler
[in] `intermediateDirectory`

 İzleme günlüğünün depolayabileceği dizin.

[in] `taskName`

 İzleme bağlamını tanımlar. Bu ad, günlük dosyası adını oluşturmak için kullanılır.

[in] `rootMarkerResponseFile`

 Kök işaretleyici içeren bir yanıt dosyasının yol adı. Kök adı bir bağlam için tüm izlemeyi gruplamak üzere kullanılır.

## <a name="return-value"></a>Dönüş değeri
 İzleme bağlamı oluşturulduysa, **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler
 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.
- [StartTrackingContext](../msbuild/starttrackingcontext.md)