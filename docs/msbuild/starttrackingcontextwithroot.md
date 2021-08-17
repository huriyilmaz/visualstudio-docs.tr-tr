---
title: StartTrackingContextWithRoot | Microsoft Docs
description: Kök işaretçisi MSBuild bir yanıt dosyası kullanarak bir izleme bağlamı başlatmak için StartTrackingContextWithRoot ile birlikte kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ec1f9b55f0a77aa1b8397820a82c78cc15d73f870e2e9144873722530fbca975
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369780"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Kök işaretçiyi belirten bir yanıt dosyası kullanarak bir izleme bağlamı başlatır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametreler

[in] `intermediateDirectory`

 İzleme günlüğünün depolan olduğu dizin.

[in] `taskName`

 İzleme bağlamını tanımlar. Bu ad, günlük dosyası adını oluşturmak için kullanılır.

[in] `rootMarkerResponseFile`

 Kök işaretçi içeren bir yanıt dosyasının yol adı. Kök ad, bir bağlamın tüm izlemelerini birlikte grup etmek için kullanılır.

## <a name="return-value"></a>Döndürülen değer

 İzleme bağlamı oluşturulduktan sonra **SUCCEEDED** bit kümesine sahip **bir HRESULT.**

## <a name="requirements"></a>Gereksinimler

 **Üst bilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [StartTrackingContext](../msbuild/starttrackingcontext.md)