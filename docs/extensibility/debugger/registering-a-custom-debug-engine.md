---
title: Özel Hata Ayıklama Motoru Kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713217"
---
# <a name="register-a-custom-debug-engine"></a>Özel hata ayıklama altyapısı kaydetme
Hata ayıklama motoru, COM kurallarını izleyerek kendisini bir sınıf fabrikası olarak kaydetmeli ve Visual Studio kayıt alt anahtarı üzerinden Visual Studio'ya kaydolmalıdır.

> [!NOTE]
> Öğretici'nin bir parçası olarak oluşturulmuş textinterpreter örneğinde hata ayıklama altyapısının nasıl kaydedildiğine bir örnek [bulabilirsiniz: ATL COM kullanarak hata ayıklama altyapısı oluşturma.](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

## <a name="dll-server-process"></a>DLL sunucu işlemi
 Hata ayıklama altyapısı genellikle kendi DLL'sinde COM sunucusu olarak ayarlanır. Bu nedenle, hata ayıklama altyapısıVisual Studio erişemeden önce kendi sınıfı fabrika CLSID COM ile kayıt gerekir. Daha sonra hata ayıklama altyapısının hata ayıklama altyapısının desteklediği herhangi bir özelliği (diğer bir şekilde ölçümler olarak da bilinir) oluşturmak için kendisini Visual Studio'ya kaydetmesi gerekir. Visual Studio kayıt defteri alt anahtarına yazılan ölçümlerin seçimi hata ayıklama altyapısının desteklediği özelliklere bağlıdır.

 [Hata ayıklama için SDK yardımcıları,](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) hata ayıklama altyapısı kaydetmek için gerekli olan kayıt defteri konumlarını değil; ayrıca, c++ geliştiricileri için kayıt defterini işlemeyi kolaylaştıran bir dizi yararlı işlevler ve bildirimler içeren *dbgmetric.lib* kitaplığını da açıklar.

### <a name="example"></a>Örnek
 Aşağıdaki örnekte (TextInterpreter örneğinden) Visual `SetMetric` Studio ile hata ayıklama motoru kaydetmek için işlevin nasıl kullanılacağını *(dbgmetric.lib'den)* gösterir. Geçirilen ölçümler *de dbgmetric.lib*tanımlanır.

> [!NOTE]
> TextInterpreter temel hata ayıklama motorudur; ayarlanmaz ve bu nedenle başka özellikler kaydolmaz. Daha eksiksiz bir hata ayıklama altyapısı, hata ayıklama altyapısının `SetMetric` desteklediği her özellik için bir arama listesiveya eşdeğeri olurdu.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Hata ayıklama için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Öğretici: ATL COM kullanarak hata ayıklama motoru oluşturma](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
