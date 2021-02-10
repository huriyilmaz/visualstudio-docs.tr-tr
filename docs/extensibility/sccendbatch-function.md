---
title: SccEndBatch Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 85d49fcd9920c442aa1736f1fb0f3e46ccd4eba0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943055"
---
# <a name="sccendbatch-function"></a>SccEndBatch işlevi
Bu işlev, kaynak denetimi işlemlerinin bir toplu işlemini sonlanır. Bu toplu işlemler iç içe olamaz.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Toplu işlem başarıyla sonuçlandırdı.|
|SCC_E_UNKNOWNERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi toplu işleri, birden çok proje veya birden çok bağlam arasında aynı kaynak denetimi işlemlerini yürütmek için kullanılır. Toplu işlem sırasında Kullanıcı deneyiminden gereksiz iletişim kutularını ortadan kaldırmak için toplu işlemler kullanılabilir. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) ve `SccEndBatch` işlevi bir işlemin başlangıcını ve sonunu belirtmek için bir çift olarak kullanılır. Bunlar iç içe geçirilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
