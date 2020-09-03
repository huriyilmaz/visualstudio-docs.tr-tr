---
title: Init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b2ed132e072d9ca8a0b9c98bfc5be6e25931805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734999"
---
# <a name="init"></a>Init
Grafik tanılama 'nın uygulama içi bileşenini, grafik bilgilerini etkin bir şekilde yakalayıp grafik günlüğü dosyasına kaydeder şekilde hazırlar.

## <a name="syntax"></a>Söz dizimi

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Parametreler
 `vsgLogGetter` Bir işlev, işlev işaretçisi, lambda veya işlev nesnesi gibi çağrılabilir bir varlık — parametre olarak geçen bir arabelleğin uzunluğu `wchar_t` ve bu arabelleğin bir işaretçisi olarak zaman alır ve döndürür `void` . Çağrıldığında, çağrılabilir varlık grafik bilgilerini kaydetmek için kullanılacak dosya adını belirler ve döndürmeden önce belirtilen arabelleğe yazar.

## <a name="remarks"></a>Açıklamalar
 `Init`İşlevi, oluşturucusunun parametresi olarak belirtilerek sınıfının bir örneği oluşturulduğunda otomatik olarak çağrılır `VsgDbg` `bDefaultInit` `true` ; Aksi halde `Init` grafik bilgilerini etkin bir şekilde yakalayıp kaydedebilmeniz için açıkça çağrılmalıdır.

 ' İ çağırarak etkin grafik günlük dosyasını sonlandırabilir ve kapatabilir ve `UnInit` sonra yeniden çağırarak yeni bir grafik günlük dosyasına daha fazla grafik bilgisi yakalayıp kaydedebilirsiniz `Init` . Aynı örneği kullanarak birkaç bağımsız grafik günlük dosyası oluşturmak istediğiniz kadar bunu yineleyebilirsiniz `VsgDbg` .

## <a name="see-also"></a>Ayrıca bkz.
- [UnInit](init.md)