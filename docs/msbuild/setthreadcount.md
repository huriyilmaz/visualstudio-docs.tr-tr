---
title: SetThreadCount | Microsoft Docs
description: MSBuild 'in genel iş parçacığı sayısını ayarlamak için SetThreadCount kullandığını ve bu sayıyı geçerli iş parçacığına atamasını öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: f7282b8c4589007492e48994628910b3a4ef0691
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966168"
---
# <a name="setthreadcount"></a>SetThreadCount

Genel iş parçacığı sayısını ayarlar ve bu sayıyı geçerli iş parçacığına atar.

## <a name="syntax"></a>Sözdizimi

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parametreler

'ndaki `threadCount`

 Kullanılacak iş parçacığı sayısı.

## <a name="return-value"></a>Döndürülen değer

 İş parçacığı sayısı güncellendiyse, **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*