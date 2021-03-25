---
title: POPLISTFUNC | Microsoft Docs
description: Dosya veya dizinlerin listesini güncelleştirmek için kaynak denetim eklentisi tarafından kullanılan POPLISTFUNC callback işlevi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aec322d73e49d4aae91956bd8df015a01c922a10
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090245"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Bu geri çağırma, IDE tarafından [SccPopulateList](../extensibility/sccpopulatelist-function.md) için sağlanır ve kaynak denetim eklentisi tarafından, bir dosya veya dizinlerin listesini güncelleştirmek için kullanılır (işleve de sağlanır `SccPopulateList` ).

 Bir Kullanıcı IDE 'de **Get** komutunu SEÇTIĞINDE, IDE kullanıcının alabilir tüm dosyaların bir liste kutusunu görüntüler. Ne yazık ki IDE, kullanıcının alabilir tüm dosyaların tam listesini bilmez; yalnızca eklentide bu liste vardır. Diğer kullanıcılar kaynak kodu denetim projesine dosya eklemiş ise, bu dosyalar listede görünmelidir, ancak IDE bunun hakkında bilgi sahibi değildir. IDE, kullanıcının alabilir olduğunu düşündüğü dosyaların bir listesini oluşturur. Bu listeyi kullanıcıya görüntülemeden önce, [](../extensibility/sccpopulatelist-function.md) `,` kaynak denetimi eklentisine, listeden dosya ekleme ve silme şansı sağlayan SccPopulateList öğesini çağırır.

## <a name="signature"></a>İmza
 Kaynak denetimi eklentisi, aşağıdaki prototiple IDE uygulanmış bir işlev çağırarak listeyi değiştirir:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametreler
 pvCallerData, `pvCallerData` çağıran tarafından geçirilen parametre (IDE) [SccPopulateList](../extensibility/sccpopulatelist-function.md)öğesine. Kaynak denetimi eklentisinin bu parametrenin içeriğiyle ilgili hiçbir şey kabul etmesi gerekir.

 fAddRemove Ise `TRUE` , `lpFileName` dosya listesine eklenmesi gereken bir dosyadır. İse `FALSE` , `lpFileName` dosya listesinden silinmesi gereken bir dosyadır.

 nStatus durumu `lpFileName` ( `SCC_STATUS` bitlerin birleşimi; Ayrıntılar Için [dosya durum koduna](../extensibility/file-status-code-enumerator.md) bakın).

 ad alanına eklenecek veya listeden Silinecek dosya adının tam dizin yolu olan lpFileName.

## <a name="return-value"></a>Döndürülen değer

|Değer|Açıklama|
|-----------|-----------------|
|`TRUE`|Eklenti bu işlevi çağırmaya devam edebilir.|
|`FALSE`|IDE tarafında (yetersiz bellek durumu gibi) ilgili bir sorun oluştu. Eklenti işlemi durdurmalıdır.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi eklentisinin dosya listesine eklemek veya silmek istediği her dosya için, bu işlevi çağırır `lpFileName` . `fAddRemove`Bayrak, listeye eklenecek yeni bir dosyayı veya silinecek eski bir dosyayı gösterir. `nStatus`Parametresi, dosyanın durumunu verir. SCC eklentisinin dosya ekleme ve silme işlemi tamamlandığında, [SccPopulateList](../extensibility/sccpopulatelist-function.md) çağrısından geri döner.

> [!NOTE]
> `SCC_CAP_POPULATELIST`Visual Studio için yetenek biti gereklidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Dosya durum kodu](../extensibility/file-status-code-enumerator.md)
