---
title: ResumeTracking | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 248bb5e5e01b8209f826478e90b2c60b70922987
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632504"
---
# <a name="resumetracking"></a>ResumeTracking

Geçerli bağlamda izlemeyi sürdürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Dönüş değeri

 İzleme devam ettirilirse, **başarılı** biti ayarlanmış bir **HRESULT** . Bağlam kullanılabilir olmadığından izleme sürdürülemediğinden **E_FAIL** döndürülür.

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [SuspendTracking](../msbuild/suspendtracking.md)