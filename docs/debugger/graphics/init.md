---
title: init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b2ed132e072d9ca8a0b9c98bfc5be6e25931805
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734999"
---
# <a name="init"></a>Init
Grafik tanılama 'nın uygulama içi bileşenini, grafik bilgilerini etkin bir şekilde yakalayıp grafik günlüğü dosyasına kaydeder şekilde hazırlar.

## <a name="syntax"></a>Sözdizimi

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Parametreler
 bir işlev, işlev işaretçisi, lambda veya işlev nesnesi gibi çağrılabilir bir varlık (örneğin, `wchar_t` ve bu arabelleğin bir işaretçisinden oluşan bir arabelleğin uzunluğu olarak geçen ve `void` döndüren) `vsgLogGetter`. Çağrıldığında, çağrılabilir varlık grafik bilgilerini kaydetmek için kullanılacak dosya adını belirler ve döndürmeden önce belirtilen arabelleğe yazar.

## <a name="remarks"></a>Açıklamalar
 @No__t_0 işlevi, oluşturucusunun `true` olarak `bDefaultInit` parametresi belirtilerek `VsgDbg` sınıfının bir örneği oluşturulduğunda otomatik olarak çağrılır; Aksi takdirde, grafik bilgilerini etkin bir şekilde yakalayıp kaydedebilmeniz için `Init` açıkça çağrılmalıdır.

 @No__t_0 çağırarak etkin grafik günlük dosyasını sonlandırabilir ve kapatabilir ve sonra `Init` yeniden çağırarak yeni bir grafik günlük dosyasına daha fazla grafik bilgisi yakalayıp kaydedebilirsiniz. Aynı `VsgDbg` örneğini kullanarak birkaç bağımsız grafik günlük dosyası oluşturmak istediğiniz kadar bunu yineleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [UnInit](init.md)