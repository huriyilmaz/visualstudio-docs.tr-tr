---
title: StopTrackingAndCleanup | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee30bf031761fa7920dadad04d8f17a1bcc0b3a2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631997"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Tüm izlemeyi durdurur ve izleme oturumu tarafından kullanılan tüm belleği serbest bırakır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Döndürülen değer

 İzleme durdurulduysa, **BAŞARILI** bit kümesiyle bir **HRESULT** döndürür.

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [StartTrackingContext](../msbuild/starttrackingcontext.md)