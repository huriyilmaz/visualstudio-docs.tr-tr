---
title: Özel hata ayıklama altyapısını kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703600"
---
# <a name="registering-a-custom-debug-engine"></a>Özel Bir Hata Ayıklama Altyapısını Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısı kendisini, Visual Studio kayıt defteri alt anahtarı aracılığıyla Visual Studio 'Ya kayıt ve COM kurallarını izleyen bir sınıf fabrikası olarak kaydetmelidir.  
  
> [!NOTE]
> Bir hata ayıklama altyapısının nasıl kaydettirileminin bir örneği, öğreticinin bir parçası olarak oluşturulan Textyorumlayıcı örneğinde bulunabilir [: atl com kullanarak hata ayıklama altyapısı oluşturma](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>DLL sunucusu işlemi  
 Genellikle, bir hata ayıklama altyapısı kendi DLL 'sinde bir COM sunucusu olarak uygulanır. Bu, hata ayıklama altyapısının, Visual Studio 'nun ona erişebilmesi için kendi sınıf fabrikasının CLSID 'sini COM ile kaydetmesi gerektiği anlamına gelir. Ardından, hata ayıklama altyapısının desteklediği herhangi bir özelliği (ölçümler olarak da bilinir) oluşturmak için hata ayıklama altyapısının kendisini Visual Studio ile kaydetmesi gerekir. Hata ayıklama altyapısının Visual Studio kayıt defteri alt anahtarına yazılan ölçümler seçimi, hata ayıklama altyapısının desteklediği özelliklere bağlıdır.  
  
 [Hata ayıklama Için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) yalnızca bir hata ayıklama altyapısını kaydetmek için gereken kayıt defteri konumlarını değil; Ayrıca, kayıt defterini daha kolay hale getirmeye yönelik bir dizi kullanışlı işlevi ve C++ geliştiricileri için bildirim içeren dbgmetric. lib kitaplığını açıklar.  
  
### <a name="example"></a>Örnek  
 Aşağıda, `SetMetric` Visual Studio ile bir hata ayıklama altyapısını kaydetmek için işlevinin (dbgmetric. lib) nasıl kullanılacağını gösteren tipik bir örnek (Textyorumlayıcı örneğinden) verilmiştir. Geçirilmekte olan ölçümler dbgmetric. lib içinde de tanımlanır.  
  
> [!NOTE]
> Textyorumlayıcı temel bir hata ayıklama altyapısıdır; uygulamaz ve bu nedenle diğer tüm özellikleri kaydetmez. Daha eksiksiz bir hata ayıklama altyapısı `SetMetric` , hata ayıklama altyapısının desteklediği her bir özellik için bir çağrı listesinin tamamını veya bunların eşdeğerini içermelidir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Hata ayıklama için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Öğretici: ATL COM kullanarak hata ayıklama altyapısı oluşturma](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
