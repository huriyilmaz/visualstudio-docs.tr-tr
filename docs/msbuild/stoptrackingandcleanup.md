---
title: StopTrackingAndCleanup | Microsoft Docs
description: İzleme oturumu MSBuild tüm izleme ve boş bellekleri serbest bırakma için StopTrackingAndCleanup'ın nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c076f0f5fbf591e0ca7ca6f91a7700185a2aea05
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142903"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

İzleme oturumu tarafından kullanılan tüm izleme ve bellek serbest bırakarak tüm izlemeleri durdurur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Döndürülen değer

 İzleme durduruldu ise BAŞARILI bit **kümesine** sahip bir **HRESULT** döndürür.

## <a name="requirements"></a>Gereksinimler

 **Üst bilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [StartTrackingContext](../msbuild/starttrackingcontext.md)