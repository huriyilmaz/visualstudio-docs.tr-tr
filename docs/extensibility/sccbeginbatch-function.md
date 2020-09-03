---
title: SccBeginBatch Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701195"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch işlevi
Bu işlev, kaynak denetimi işlemleri toplu işlem dizisini başlatır. Toplu işi sonlandırmak için [SccEndBatch](../extensibility/sccendbatch-function.md) çağırılır. Bu toplu işlemler iç içe olamaz.

## <a name="syntax"></a>Söz dizimi

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlem toplu işlemleri başarıyla başlatıldı.|
|SCC_E_UNKNOWNERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi toplu işleri, birden çok proje veya birden çok bağlam arasında aynı işlemleri yürütmek için kullanılır. Toplu işlem sırasında kullanıcı deneyiminin gereksiz proje başına iletişim kutularını ortadan kaldırmak için toplu işlemler kullanılabilir. `SccBeginBatch`İşlevi ve [SccEndBatch](../extensibility/sccendbatch-function.md) , bir işlemin başlangıcını ve sonunu belirtmek için bir işlev çifti olarak kullanılır. Bunlar iç içe geçirilemez. `SccBeginBatch` bir toplu işlemin devam ettiğini belirten bir bayrak ayarlar.

 Bir toplu işlem etkinken, kaynak denetimi eklentisinin kullanıcıya herhangi bir soru için en çok bir iletişim kutusu sunması ve sonraki tüm işlemlerde bu iletişim kutusundan yanıtı uygulamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
