---
description: Bu işlev, kaynak denetimi eklentisinin kapanmasından dolayı bir önceki SccInitialize çağrısıyla oluşturulan tüm ayırmaları veya açık bağlantıları temizler.
title: Sccunınitialize Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 7d387167e2032cbb253e86f8d67da38f99fc1076
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063779"
---
# <a name="sccuninitialize-function"></a>SccUninitialize İşlevi
Bu işlev, kaynak denetimi eklentisinin kapanmasından dolayı bir önceki [SccInitialize](../extensibility/sccinitialize-function.md) çağrısıyla oluşturulan tüm ayırmaları veya açık bağlantıları temizler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

'ndaki [SccInitialize](../extensibility/sccinitialize-function.md)içinde oluşturulan kaynak denetimi eklentisi bağlam yapısına yönelik işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Temizleme işlemi başarıyla tamamlandı.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi eklentisi kapanmaya hazırlanmaktan ve eklentinin bağlam yapısına ayrılan bellek boşaltmasından sorumludur. Bu işlev, bir eklentinin verilen her örneği için bir kez çağrılır. [SccInitialize](../extensibility/sccinitialize-function.md) çağrısı bu çağrıdan önce gelir. Çağrısı sırasında hiç proje hala açık olamaz `SccUninitialize` .

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
