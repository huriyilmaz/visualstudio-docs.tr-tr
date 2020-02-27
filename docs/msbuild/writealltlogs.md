---
title: WriteAllTLogs | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eadb30ee25b1182be5deb12feebd5ef280ebf4b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630684"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Tüm iş parçacıkları ve bağlamlar için izleme günlüklerini yazar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametreler

[in] `intermediateDirectory`

 İzleme günlüğünün depolayabileceği dizin.

[in] `tlogRootName`

 Günlük dosyası adının kök adı.

## <a name="return-value"></a>Dönüş değeri

 İzleme bağlamı oluşturulduysa, **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)