---
title: ResumeTracking | Microsoft Docs
description: Geçerli bağlamda izlemeyi sürdüren ResumeTracking MSBuild söz dizimi, gereksinimleri ve dönüş değerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 6b2d7b4bd0bdbdf60864344edb552c884482a93e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143059"
---
# <a name="resumetracking"></a>ResumeTracking

İzlemeyi geçerli bağlamda sürdürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Döndürülen değer

 İzleme devam ettiyse **BAŞARILI** bit kümesine sahip **bir HRESULT.** **E_FAIL,** bağlam kullanılabilir olduğundan izleme sürdürülenene kadar döndürülür.

## <a name="requirements"></a>Gereksinimler

 **Üst bilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [SuspendTracking](../msbuild/suspendtracking.md)