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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e7de3572b17bf47859a64451149a269988c91e5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836689"
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
