---
title: Init | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea9f8a24d342668b3574c3798a32c58c124aca7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185853"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik tanılama 'nın uygulama içi bileşenini, grafik bilgilerini etkin bir şekilde yakalayıp grafik günlüğü dosyasına kaydeder şekilde hazırlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `vsgLogGetter`  
 Bir işlev, işlev işaretçisi, lambda veya işlev nesnesi gibi çağrılabilir bir varlık — parametre olarak geçen bir arabelleğin uzunluğu `wchar_t` ve bu arabelleğin bir işaretçisi olarak zaman alır ve döndürür `void` . Çağrıldığında, çağrılabilir varlık grafik bilgilerini kaydetmek için kullanılacak dosya adını belirler ve döndürmeden önce belirtilen arabelleğe yazar.  
  
## <a name="remarks"></a>Açıklamalar  
 `Init`İşlevi, oluşturucusunun parametresi olarak belirtilerek sınıfının bir örneği oluşturulduğunda otomatik olarak çağrılır `VsgDbg` `bDefaultInit` `true` ; Aksi halde `Init` grafik bilgilerini etkin bir şekilde yakalayıp kaydedebilmeniz için açıkça çağrılmalıdır.  
  
 ' İ çağırarak etkin grafik günlük dosyasını sonlandırabilir ve kapatabilir ve `UnInit` sonra yeniden çağırarak yeni bir grafik günlük dosyasına daha fazla grafik bilgisi yakalayıp kaydedebilirsiniz `Init` . Aynı örneği kullanarak birkaç bağımsız grafik günlük dosyası oluşturmak istediğiniz kadar bunu yineleyebilirsiniz `VsgDbg` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UnInit](../debugger/init.md)
