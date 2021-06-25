---
description: Bu işlev, kaynak denetim eklentiyi kapatmaya hazırlık olarak önceki bir SccInitialize çağrısı tarafından oluşturulan ayırmaları veya açık bağlantıları temizler.
title: SccUninitialize İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d46aedd3e962d0684689ff29a34061b777fe08e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904080"
---
# <a name="sccuninitialize-function"></a>SccUninitialize İşlevi
Bu işlev, kaynak denetim eklentiyi kapatmaya hazırlık olarak [önceki bir SccInitialize](../extensibility/sccinitialize-function.md) çağrısı tarafından oluşturulan ayırmaları veya açık bağlantıları temizler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

[in] [SccInitialize](../extensibility/sccinitialize-function.md)içinde oluşturulan kaynak denetimi eklentisi bağlam yapısının işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Temizleme başarıyla tamamlandı.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi eklentisi, kapatmaya hazırlanma ve eklentinin bağlam yapısı için ayırmış olduğu belleği serbest bırakarak sorumludur. İşlev, bir eklentinin verilen her örneği için bir kez çağrılır. Bu çağrıdan [önce SccInitialize](../extensibility/sccinitialize-function.md) çağrısı yer almaktadır. çağrısında hiçbir proje hala açık `SccUninitialize` olmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
