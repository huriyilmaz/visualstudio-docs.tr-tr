---
title: SetThreadCount | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 102f46ec639719bb2bec70a38c6c7177c63793c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632335"
---
# <a name="setthreadcount"></a>SetThreadCount

Genel iş parçacığı sayısını ayarlar ve geçerli iş parçacığına bu sayıyı atar.

## <a name="syntax"></a>Sözdizimi

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parametreler

[içinde]`threadCount`

 Kullanılacak iş parçacığı sayısı.

## <a name="return-value"></a>Döndürülen değer

 İş parçacığı sayısı **güncelleştirildiyse, BAŞARILI** bit kümesine sahip bir **HRESULT.**

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker.h*