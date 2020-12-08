---
title: Özel hata ayıklama altyapısını kaydetme | Microsoft Docs
description: Hata ayıklama altyapısının kendisini bir sınıf fabrikası olarak kaydetme, COM kurallarını izleyen ve kayıt defteri aracılığıyla Visual Studio ile kaydetme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 01d7190bbf087bb60ac670341d82078e94c81c52
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847188"
---
# <a name="register-a-custom-debug-engine"></a>Özel bir hata ayıklama altyapısını kaydetme
Hata ayıklama altyapısı kendisini bir sınıf fabrikası olarak kaydetmelidir, COM kurallarını ve Visual Studio kayıt defteri alt anahtarı aracılığıyla Visual Studio 'Ya kaydolmalıdır.

> [!NOTE]
> Bir hata ayıklama altyapısını, öğreticinin bir parçası olarak oluşturulan Textyorumlayıcı örneğinde nasıl kaydedebileceğinizi gösteren bir örnek bulabilirsiniz [: atl com kullanarak hata ayıklama altyapısı oluşturma](/previous-versions/bb147024(v=vs.90)).

## <a name="dll-server-process"></a>DLL sunucusu işlemi
 Hata ayıklama altyapısı genellikle kendi DLL 'sinde bir COM sunucusu olarak ayarlanır. Bu nedenle, Visual Studio 'nun erişebilmesi için hata ayıklama altyapısının CLSID 'sini COM ile kaydetmesi gerekir. Daha sonra hata ayıklama altyapısının, hata ayıklama altyapısının desteklediği herhangi bir özelliği (ölçümler olarak da bilinir) oluşturmak için kendisini Visual Studio ile kaydetmesi gerekir. Visual Studio kayıt defteri alt anahtarına yazılan ölçümler seçimi, hata ayıklama altyapısının desteklediği özelliklere bağlıdır.

 [Hata ayıklama Için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) yalnızca bir hata ayıklama altyapısını kaydetmek için gereken kayıt defteri konumlarını değil; Ayrıca, kayıt defterini daha kolay hale getirmeye yönelik bir dizi kullanışlı işlevi ve C++ geliştiricileri için bildirim içeren *dbgmetric. lib* kitaplığını açıklar.

### <a name="example"></a>Örnek
 Aşağıdaki örnek (Textyorumlayıcı örneğinden), `SetMetric` Visual Studio ile bir hata ayıklama altyapısını kaydetmek için işlevinin ( *dbgmetric. lib*) nasıl kullanılacağını gösterir. Geçirilmekte olan ölçümler *dbgmetric. lib* içinde de tanımlanır.

> [!NOTE]
> Textyorumlayıcı temel bir hata ayıklama altyapısıdır; ayarlanmamış — ve bu nedenle, diğer tüm özellikleri kaydetmez. Daha eksiksiz bir hata ayıklama altyapısı `SetMetric` , hata ayıklama altyapısının desteklediği her bir özellik için bir çağrı listesinin tamamını veya bunların eşdeğerini içermelidir.

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
- [Öğretici: ATL COM kullanarak hata ayıklama altyapısı oluşturma](/previous-versions/bb147024(v=vs.90))