---
title: SetThreadCount | Microsoft Docs
description: MSBuild, genel iş parçacığı sayısını ayarlamak için setthreadcount 'ı nasıl kullandığını ve bu sayıyı geçerli iş parçacığına atamayı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084824"
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