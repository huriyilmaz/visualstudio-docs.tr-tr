---
title: ResumeTracking | Microsoft Docs
description: Geçerli bağlamda izlemeye devam eden MSBuild ResumeTracking için sözdizimi, gereksinimler ve dönüş değeri hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: fd6722ca0b930d66a386732dac466a8e4fe36976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937920"
---
# <a name="resumetracking"></a>ResumeTracking

Geçerli bağlamda izlemeyi sürdürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Döndürülen değer

 İzleme devam ettirilirse, **başarılı** biti ayarlanmış bir **HRESULT** . Bağlam kullanılabilir olmadığından izleme sürdürülemediğinden **E_FAIL** döndürülür.

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [SuspendTracking](../msbuild/suspendtracking.md)