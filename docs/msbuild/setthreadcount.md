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
ms.openlocfilehash: 1f8e3792015696f5424ffe9134a78b1b88f780e5622e2292382bc5b18ff80cad
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121257491"
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