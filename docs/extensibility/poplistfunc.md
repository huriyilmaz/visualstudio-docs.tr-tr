---
title: POPLISTFUNC | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702071"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Bu geri arama, IDE tarafından [SccPopulateList'e](../extensibility/sccpopulatelist-function.md) verilir ve kaynak denetim eklentisi tarafından dosya veya dizin listesini `SccPopulateList` güncelleştirmek için kullanılır (ayrıca işleve verilir).

 Bir kullanıcı IDE'de **Get** komutunu seçtiğinde, IDE kullanıcının alabilecekleri tüm dosyaların bir liste kutusunu görüntüler. Ne yazık ki, IDE kullanıcının alabilecekleri tüm dosyaların tam listesini bilmiyor; yalnızca eklentide bu liste vardır. Diğer kullanıcılar kaynak kodu denetimi projesine dosya eklediyse, bu dosyalar listede görünmelidir, ancak IDE bunlar hakkında bilgi sahibi değildir. IDE, kullanıcının alabileceğinizi düşündüğü dosyaların bir listesini oluşturur. Bu listeyi kullanıcıya görüntülemeden önce, kaynak denetimi eklentisine listeden dosya ekleme ve silme şansı veren [SccPopulateList'i](../extensibility/sccpopulatelist-function.md) `,` çağırır.

## <a name="signature"></a>İmza
 Kaynak denetim eklentisi, aşağıdaki prototiple IDE tarafından uygulanan bir işlevi arayarak listeyi değiştirir:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametreler
 pvCallerData `pvCallerData` Arayan (IDE) tarafından [SccPopulateList'e](../extensibility/sccpopulatelist-function.md)geçirilen parametre. Kaynak denetimi eklentisi bu parametrenin içeriği hakkında hiçbir şey üstlenmemelidir.

 fAddRemove `TRUE`If `lpFileName` , dosya listesine eklenmesi gereken bir dosyadır. , `FALSE` `lpFileName` dosya listesinden silinmesi gereken bir dosyaysa.

 nDurum Durumu `lpFileName` `SCC_STATUS` (bitlerin bir leşimi; ayrıntılar için [Dosya Durum Kodu'na](../extensibility/file-status-code-enumerator.md) bakın).

 lpFileName Dosya adının tam dizin yolu eklemek veya listeden silmek.

## <a name="return-value"></a>Döndürülen değer

|Değer|Açıklama|
|-----------|-----------------|
|`TRUE`|Eklenti bu işlevi aramaya devam edebilir.|
|`FALSE`|IDE tarafında bir sorun (bellek dışı bir durum gibi) olmuştur. Eklenti işlemi durdurmalıdır.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetim eklentisinin dosya listesine eklemek veya silmek istediği her dosya için, `lpFileName`bu işlevi çağırır ve .. Bayrak, `fAddRemove` listeye eklenecek yeni bir dosyayı veya silinecek eski bir dosyayı gösterir. `nStatus` Parametre dosyanın durumunu verir. SCC eklentisi dosya eklemeyi ve silmeyi bitirdiğinde, [SccPopulateList](../extensibility/sccpopulatelist-function.md) çağrısından döner.

> [!NOTE]
> Visual `SCC_CAP_POPULATELIST` Studio için özellik biti gereklidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri arama işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Dosya durum kodu](../extensibility/file-status-code-enumerator.md)
