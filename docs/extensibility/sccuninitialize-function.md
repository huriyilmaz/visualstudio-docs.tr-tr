---
title: SccUninitialize Fonksiyonu | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700237"
---
# <a name="sccuninitialize-function"></a>SccUninitialize İşlevi
Bu işlev, kaynak denetim eklentisini kapatmaya hazırlık olarak [SccInitialize'ye](../extensibility/sccinitialize-function.md) yapılan önceki bir çağrı tarafından oluşturulan ayırmaları veya açık bağlantıları temizler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

[içinde] [SccInitialize](../extensibility/sccinitialize-function.md)oluşturulan kaynak denetimi eklentisi bağlam yapısı için işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Temizleme başarıyla tamamlandı.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetim eklentisi, kapatmaya hazırlanmasından ve eklentinin bağlam yapısına ayırdığı belleği serbest düşürmekten sorumludur. İşlev, verilen her bir eklenti örneği için bir kez çağrılır. [SccInitialize'a](../extensibility/sccinitialize-function.md) yapılan bir çağrı bu çağrıdan önce gelir. Çağrı sırasında hiçbir proje hala açık `SccUninitialize`olamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
