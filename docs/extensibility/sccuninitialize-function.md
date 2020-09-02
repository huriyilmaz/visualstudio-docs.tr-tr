---
title: Sccunınitialize Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700237"
---
# <a name="sccuninitialize-function"></a>SccUninitialize İşlevi
Bu işlev, kaynak denetimi eklentisinin kapanmasından dolayı bir önceki [SccInitialize](../extensibility/sccinitialize-function.md) çağrısıyla oluşturulan tüm ayırmaları veya açık bağlantıları temizler.

## <a name="syntax"></a>Söz dizimi

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
