---
title: Askıya Alma Takibi | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 950c6a07a46f7f4b970912e576257a577021367e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632024"
---
# <a name="suspendtracking"></a>SuspendTracking

Geçerli bağlamda izlemeyi askıya adamaktadır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Döndürülen değer

 İzleme askıya **alındıysa, BAŞARILI** bit kümesine sahip bir **HRESULT.**

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [ResumeTracking](../msbuild/resumetracking.md)