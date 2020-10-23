---
title: EndTrackingContext | Microsoft Docs
description: Geçerli izleme bağlamını sonlandırmak için, MSBuild EndTrackingContext ' i kullanmak için sözdizimi, dönüş değeri ve gereksinimleri öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da1ef921106732a7787f68a979bc88f3ac012b6d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436665"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Geçerli izleme bağlamını sonlandırın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Döndürülen değer

İzleme bağlamı sonlandırıldıysa, **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler

**Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
