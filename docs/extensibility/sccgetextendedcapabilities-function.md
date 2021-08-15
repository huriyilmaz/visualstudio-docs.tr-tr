---
description: Bu işlev, kaynak denetimi eklentisi tarafından desteklenen ek özellikleri döndürür.
title: Sccgebir Dedcapabilities Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 986a5f33b4b2476cc327b5e2e4b287f1e29cc5d95487d61ace6ebf22e9d23916
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321057"
---
# <a name="sccgetextendedcapabilities-function"></a>Sccgebir Dedcapabilities işlevi
Bu işlev, kaynak denetimi eklentisi tarafından desteklenen ek özellikleri döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parametreler
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 lSccExCaps

'ndaki Test edilecek genişletilmiş bir özellik belirten bayrak (olası bayraklar için [yetenek bayraklarıyla](../extensibility/capability-flags.md) genişletilmiş yetenek kodu tablosuna bakın).

 PBX destekleniyor

dışı `TRUE`Belirtilen yetenek destekleniyorsa sıfır olmayan () döndürür; Aksi takdirde, sıfır ( `FALSE` ) döndürür.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Özellik al işlemi başarıyla tamamlandı.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Bilinmeyen veya belirtilmeyen bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Bu yöntem isteğe bağlı olarak çağrılır; diğer bir deyişle, bir özelliğin test olması gerektiğinde, bu özelliğin desteklenip desteklenmediğini tespit etmek için bu yöntem çağrılır. Tek seferde yalnızca bir bayrak belirtildi.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Hata kodları](../extensibility/error-codes.md)
- [Yetenek bayrakları](../extensibility/capability-flags.md)
