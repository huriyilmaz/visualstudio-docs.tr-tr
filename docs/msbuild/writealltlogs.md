---
title: WriteAllTLogs | Microsoft Docs
description: Tüm iş parçacıkları ve bağlamlar için izleme günlüklerini yazan WriteAllTLogs için sözdizimi, gereksinimler ve dönüş değeri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65e0610c8148ab6ff32d8c19f6fd378ba46d76d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933602"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Tüm iş parçacıkları ve bağlamlar için izleme günlüklerini yazar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametreler

'ndaki `intermediateDirectory`

 İzleme günlüğünün depolayabileceği dizin.

'ndaki `tlogRootName`

 Günlük dosyası adının kök adı.

## <a name="return-value"></a>Döndürülen değer

 İzleme bağlamı oluşturulduysa, **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)