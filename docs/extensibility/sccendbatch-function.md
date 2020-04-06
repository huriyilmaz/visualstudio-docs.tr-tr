---
title: SccEndBatch Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700918"
---
# <a name="sccendbatch-function"></a>SccEndBatch fonksiyonu
Bu işlev, kaynak denetim işlemleri bir toplu sonuçlandırır. Bu gruplar iç içe geçmeyebilir.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Bir dizi operasyon başarıyla sonuçlandı.|
|SCC_E_UNKNOWNERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetim toplu işlemleri, birden çok proje veya birden çok bağlam da aynı kaynak denetimi işlemlerini yürütmek için kullanılır. Toplu iş, toplu işlem sırasında gereksiz iletişim kutularını kullanıcı deneyiminden ortadan kaldırmak için kullanılabilir. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) ve `SccEndBatch` işlev, bir işlemin başlangıcını ve sonunu belirtmek için bir çift olarak kullanılır. İç içe geçemezler.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
