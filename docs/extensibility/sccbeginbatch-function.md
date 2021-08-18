---
description: Bu işlev, kaynak denetimi işlemlerinin toplu dizisini başlatır.
title: SccBeginBatch İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fc1d78840915899181046d3e1bfb19d554751c1a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144606"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch işlevi
Bu işlev, kaynak denetimi işlemlerinin toplu dizisini başlatır. Toplu [işi sona erdirecek SccEndBatch](../extensibility/sccendbatch-function.md) çağrılır. Bu toplu işler iç içe geçmiş olabilir.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Toplu işlemler başarıyla başlatıldı.|
|SCC_E_UNKNOWNERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi toplu işleri, aynı işlemleri birden çok proje veya birden çok bağlam üzerinde yürütmek için kullanılır. Toplu işlem sırasında kullanıcı deneyiminden proje başına yedekli iletişim kutularını ortadan kaldırmak için toplu işler kullanılabilir. işlevi `SccBeginBatch` ve [SccEndBatch,](../extensibility/sccendbatch-function.md) bir işlem başlangıcını ve sonunu göstermek için işlev çifti olarak kullanılır. Bunlar iç içe olamaz. `SccBeginBatch` , toplu işlem devam ediyor olduğunu belirten bir bayrak ayarlar.

 Toplu işlem geçerliyken, kaynak denetim eklentisi kullanıcıya herhangi bir soru için en fazla bir iletişim kutusu sunmalıdır ve sonraki tüm işlemlere bu iletişim kutusundan gelen yanıtı uygulamalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
