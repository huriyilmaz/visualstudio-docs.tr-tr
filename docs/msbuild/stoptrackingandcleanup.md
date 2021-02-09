---
title: StopTrackingAndCleanup | Microsoft Docs
description: MSBuild 'in tüm izlemeyi durdurmak ve izleme oturumu tarafından kullanılan belleği boşaltmak için StopTrackingAndCleanup komutunu nasıl kullandığını öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 5e74e44289e4fd04acf82170584af8645767b63e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905230"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Tüm izlemeyi durduruyor ve izleme oturumu tarafından kullanılan belleği serbest bırakır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Döndürülen değer

 İzleme durdurulmuşsa, **başarılı** biti ayarlanmış bir **HRESULT** döndürür.

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [StartTrackingContext](../msbuild/starttrackingcontext.md)