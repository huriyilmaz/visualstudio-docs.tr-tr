---
title: Init | Microsoft Docs
description: Grafik tanılama 'nın uygulama içi bileşenini grafik bilgilerini günlüğe kaydetmek üzere hazırlamak için VsgDbg öğesinin Init () yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d7aab5c2ddb35f1158aa83a4a365e5a0594ce457
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133828"
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
 `vsgLogGetter` Bir işlev, işlev işaretçisi, lambda veya işlev nesnesi gibi çağrılabilir bir varlık — parametre olarak geçen bir arabelleğin uzunluğu `wchar_t` ve bu arabelleğin bir işaretçisi olarak zaman alır ve döndürür `void` . Çağrıldığında, çağrılabilir varlık grafik bilgilerini kaydetmek için kullanılacak dosya adını belirler ve döndürmeden önce belirtilen arabelleğe yazar.

## <a name="remarks"></a>Açıklamalar
 `Init`İşlevi, oluşturucusunun parametresi olarak belirtilerek sınıfının bir örneği oluşturulduğunda otomatik olarak çağrılır `VsgDbg` `bDefaultInit` `true` ; Aksi halde `Init` grafik bilgilerini etkin bir şekilde yakalayıp kaydedebilmeniz için açıkça çağrılmalıdır.

 ' İ çağırarak etkin grafik günlük dosyasını sonlandırabilir ve kapatabilir ve `UnInit` sonra yeniden çağırarak yeni bir grafik günlük dosyasına daha fazla grafik bilgisi yakalayıp kaydedebilirsiniz `Init` . Aynı örneği kullanarak birkaç bağımsız grafik günlük dosyası oluşturmak istediğiniz kadar bunu yineleyebilirsiniz `VsgDbg` .

## <a name="see-also"></a>Ayrıca bkz.
- [UnInit](init.md)