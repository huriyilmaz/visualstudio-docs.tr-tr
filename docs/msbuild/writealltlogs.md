---
title: WriteAllTLogs | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630684"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Tüm iş parçacıkları ve bağlamlar için izleme günlükleri yazar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametreler

[içinde]`intermediateDirectory`

 İzleme günlüğünün depolandığı dizini.

[içinde]`tlogRootName`

 Günlük dosya adının kök adı.

## <a name="return-value"></a>Döndürülen değer

 İzleme bağlamı **oluşturulduysa, BAŞARILI** bit kümesine sahip bir **HRESULT.**

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)