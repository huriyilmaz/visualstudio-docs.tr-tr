---
title: SuspendTracking | Microsoft Docs
description: geçerli bağlamda izlemeyi askıya alacak MSBuild SuspendTracking için sözdizimi, gereksinimler ve dönüş değeri öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 420ba1fd7cc4285d638cf4d82b4e9d1d7f0ad23bfc6d5c23331ebe1ba3964dbd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397273"
---
# <a name="suspendtracking"></a>SuspendTracking

Geçerli bağlamda izlemeyi askıya alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Döndürülen değer

 İzleme askıya alınmışsa **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [ResumeTracking](../msbuild/resumetracking.md)