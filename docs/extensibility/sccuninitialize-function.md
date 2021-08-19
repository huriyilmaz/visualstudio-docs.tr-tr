---
description: Bu işlev, kaynak denetimi eklentiyi kapatmaya hazırlık olarak önceki bir SccInitialize çağrısı tarafından oluşturulan ayırmaları veya açık bağlantıları temizler.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 56d2365df1e613976943bd8ba33f6d49a32566f5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117598"
---
# <a name="sccuninitialize-function"></a>SccUninitialize İşlevi
Bu işlev, kaynak denetimi eklentiyi kapatmaya hazırlık olarak [önceki bir SccInitialize](../extensibility/sccinitialize-function.md) çağrısı tarafından oluşturulan ayırmaları veya açık bağlantıları temizler.

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
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Temizleme başarıyla tamamlandı.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi eklentisi, kapatmaya hazırlanma ve eklentinin bağlam yapısı için ayırmış olduğu belleği serbest bırakarak sorumludur. İşlev, bir eklentinin verilen her örneği için bir kez çağrılır. Bu çağrıdan [önce SccInitialize](../extensibility/sccinitialize-function.md) çağrısı yer almaktadır. çağrısında hiçbir proje hala açık `SccUninitialize` olmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
