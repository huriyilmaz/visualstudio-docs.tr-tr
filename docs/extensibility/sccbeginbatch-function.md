---
title: SccBeginBatch Fonksiyonu | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701195"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch fonksiyonu
Bu işlev, kaynak denetim işlemlerinin toplu sırasını başlatır. [SccEndBatch](../extensibility/sccendbatch-function.md) toplu iş sona erdirmek için çağrılacak. Bu gruplar iç içe geçmeyebilir.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Toplu işlemler başarıyla başladı.|
|SCC_E_UNKNOWNERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetim toplu işlemleri, birden çok proje veya birden çok bağlam da aynı işlemleri yürütmek için kullanılır. Toplu iş, toplu işlem sırasında kullanıcı deneyiminden proje başına gereksiz iletişim kutularını ortadan kaldırmak için kullanılabilir. İşlev `SccBeginBatch` ve [SccEndBatch,](../extensibility/sccendbatch-function.md) bir işlemin başlangıcını ve sonunu belirtmek için işlev çifti olarak kullanılır. İç içe geçemezler. `SccBeginBatch`toplu iş işleminin devam ettiğini belirten bir bayrak ayarlar.

 Toplu işlem etkinken, kaynak denetimi eklentisi kullanıcıya herhangi bir soru için en fazla bir iletişim kutusunda sunmalı ve sonraki tüm işlemlerde bu iletişim kutusundan gelen yanıtı uygulamalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
