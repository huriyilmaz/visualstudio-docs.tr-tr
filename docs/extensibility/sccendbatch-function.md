---
description: Bu işlev, kaynak denetimi işlemlerinin bir toplu işlemini sonlanır.
title: SccEndBatch Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a608f05cada958a56f3fb5403793c70f5ece5ba9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124431"
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
