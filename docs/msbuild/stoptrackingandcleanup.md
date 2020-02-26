---
title: StopTrackingAndCleanup | Microsoft Docs
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
ms.openlocfilehash: 4a80fcde7aeab601791c033bd21effce175b2cb9
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579568"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Tüm izlemeyi durduruyor ve izleme oturumu tarafından kullanılan belleği serbest bırakır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Dönüş değeri
 İzleme durdurulmuşsa, **başarılı** biti ayarlanmış bir **HRESULT** döndürür.

## <a name="requirements"></a>Gereksinimler
 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.
- [StartTrackingContext](../msbuild/starttrackingcontext.md)