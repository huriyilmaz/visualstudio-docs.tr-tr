---
title: SetThreadCount | Microsoft Docs
description: Genel MSBuild sayısını ayarlamak ve bu s sayımı geçerli iş parçacığına atamak için SetThreadCount'un nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 35649f2ae7c0aec8b713573fc5b9f8f29e86ac2f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625551"
---
# <a name="setthreadcount"></a>SetThreadCount

Genel iş parçacığı sayısını ayarlar ve bu s sayımı geçerli iş parçacığına atar.

## <a name="syntax"></a>Sözdizimi

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parametreler

[in] `threadCount`

 Kullanılan iş parçacığı sayısı.

## <a name="return-value"></a>Döndürülen değer

 İş parçacığı sayısı **güncelleştirilmişse BAŞARILI** bit kümesine sahip **bir HRESULT.**

## <a name="requirements"></a>Gereksinimler

 **Üst bilgi:** *FileTracker.h*