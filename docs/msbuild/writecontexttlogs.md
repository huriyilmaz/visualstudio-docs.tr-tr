---
title: WriteContextTLogs | Microsoft Docs
description: Geçerli bağlam için günlük dosyalarını yazan WriteContextTLogs için söz dizimi, gereksinimler ve dönüş değerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 32f692012c5a60caf4988142b03b5610a0ebf717
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076977"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Geçerli bağlam için günlük dosyalarını yazar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametreler

[in] `intermediateDirectory`

 İzleme günlüğünün depolan olduğu dizin.

[in] `tlogRootName`

 Günlük dosyası adının kök adı.

## <a name="return-value"></a>Döndürülen değer

 İzleme bağlamı oluşturulduktan sonra **SUCCEEDED** bit kümesine sahip **bir HRESULT.**

## <a name="requirements"></a>Gereksinimler

 **Üst bilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [WriteAllTLogs](../msbuild/writealltlogs.md)