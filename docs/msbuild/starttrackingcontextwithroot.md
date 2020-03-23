---
title: Başlangıç İzlemeBağlamWithRoot | Microsoft Dokümanlar
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
ms.openlocfilehash: 68d585361b9797bf1df9c8b0b31f8a089e9de025
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632101"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Kök işaretçisi belirten bir yanıt dosyanı kullanarak izleme bağlamı başlatır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametreler

[içinde]`intermediateDirectory`

 İzleme günlüğünün depolandığı dizini.

[içinde]`taskName`

 İzleme bağlamını tanımlar. Bu ad, günlük dosyası adını oluşturmak için kullanılır.

[içinde]`rootMarkerResponseFile`

 Kök işaretçisi içeren yanıt dosyasının yol adı. Kök adı, tüm izlemeyi bir bağlam için gruplandırmak için kullanılır.

## <a name="return-value"></a>Döndürülen değer

 İzleme bağlamı **oluşturulduysa, BAŞARILI** bit kümesine sahip bir **HRESULT.**

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [StartTrackingContext](../msbuild/starttrackingcontext.md)