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
ms.openlocfilehash: 7c64f0079a03b730fb700cfbc6320c5dffa05d7a
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579508"
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