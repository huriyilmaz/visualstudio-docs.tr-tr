---
title: 'Nasıl yapılır: özel metin Işaretçileri oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780958"
---
# <a name="how-to-create-custom-text-markers"></a>Nasıl yapılır: Özel Metin İşaretçileri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodu vurgulamak veya düzenlemek için özel bir metin işaretleyicisi oluşturmak istiyorsanız aşağıdaki adımları uygulamanız gerekir:  
  
- Diğer araçların erişebilmesi için yeni metin işaretçisini Kaydet  
  
- Metin işaretçisinin varsayılan bir uygulamasını ve yapılandırmasını sağlama  
  
- Metin işaretleyicisini kullanmak için diğer süreçler tarafından kullanılabilecek bir hizmet oluşturun  
  
  Bir kod bölgesine metin işaretçisi uygulama hakkında ayrıntılar için bkz. [nasıl yapılır: metin Işaretleyicileri kullanma](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Özel bir işaret kaydetmek için  
  
1. Aşağıda gösterildiği gibi bir kayıt defteri girişi oluşturun:  
  
    HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \ metin Editor\External işaretçileri\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>`GUID`eklenmekte olan işaretçiyi tanımlamak için kullanılır  
  
    *\<Version>* , sürümüdür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , örneğin 8,0  
  
    *\<PackageGUID>* , Otomasyon nesnesini uygulayan VSPackage 'un GUID 'sidir.  
  
   > [!NOTE]
   > HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio 'ın kök yolu, \\ *\<Version>* Visual Studio Kabuğu başlatıldığında alternatif bir kök ile geçersiz kılınabilir, daha fazla bilgi için bkz. [komut satırı anahtarları](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \ metin Editor\External işaretçileri altında dört değer oluşturun\\*\<MarkerGUID>*  
  
   - (Varsayılan)  
  
   - Hizmet  
  
   - DisplayName  
  
   - Paket  
  
   - `Default` REG_SZ türünde isteğe bağlı bir giriştir. Ayarlandığında, girişin değeri, bazı yararlı tanımlama bilgilerini içeren bir dizedir, örneğin "özel metin Işaretleyicisi".  
  
   - `Service` , özel metin işaretleyicisini sağlayan hizmetin GUID dizesini içeren REG_SZ türünde bir giriştir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . Biçim {XXXXXX XXXX XXXX XXXX XXXXXXXXX} biçimindedir.  
  
   - `DisplayName` , özel metin işaretçisinin adının kaynak KIMLIĞINI içeren REG_SZ türünde bir giriştir. Biçim #YYYY.  
  
   - `Package``GUID`hizmet altında listelenen VSPackage 'ı içeren REG_SZ türünde bir giriştir. Biçim {XXXXXX XXXX XXXX XXXX XXXXXXXXX} biçimindedir.  
  
### <a name="to-create-a-custom-text-marker"></a>Özel metin işaretçisi oluşturmak için  
  
1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> arabirimini gerçekleştirin.  
  
     Bu arabirimin uygulamanız, özel işaret türünün davranışını ve görünümünü tanımlar.  
  
     Bu arabirim şu durumlarda çağrılır  
  
    1. Bir Kullanıcı IDE 'yi ilk kez başlatır.  
  
    2. Kullanıcı, IDE 'nin **Araçlar** menüsünden alınan **Seçenekler** iletişim kutusunun sol bölmesinde bulunan **ortam** klasöründeki **yazı tipleri ve renkler** Özellik sayfası altındaki **varsayılan ayarları Sıfırla** düğmesini seçer.  
  
2. Yöntem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> `IVsPackageDefinedTextMarkerType` çağrısında belirtilen işaret türü GUID 'sine bağlı olarak hangi uygulamanın döndürüleceğini belirten yöntemini uygulayın.  
  
     Ortam, özel işaret türü ilk kez oluşturulduğunda bu yöntemi çağırır ve özel işaret türünü tanımlayan bir GUID belirtir.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>İşaretleyici türü bir hizmet olarak temin etmek için  
  
1. Yöntemini çağırın <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> .  
  
     İçin bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> döndürülür.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A>Özel işaret türü hizmetinizi tanımlayan ve arabirimin uygulamanıza yönelik bir işaretçi sağlayan GUID 'yi belirterek yöntemi çağırın <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> . <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>Uygulamanız, arabirimi uygulamanıza bir işaretçi döndürmelidir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> .  
  
     Hizmetinizin döndürüldüğünü tanımlayan benzersiz bir tanımlama bilgisi. Daha sonra bu tanımlama bilgisi <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> değerini belirten arabirimin yöntemini çağırarak özel işaretleyici türü hizmetinizi iptal etmek için bu tanımlama bilgisini kullanabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski API ile metin Işaretleyicileri kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Nasıl yapılır: standart metin Işaretçileri ekleme](../extensibility/how-to-add-standard-text-markers.md)   
 [Nasıl yapılır: hata Işaretleyicileri uygulama](../extensibility/how-to-implement-error-markers.md)   
 [Nasıl Yapılır: Metin İşaretçileri Kullanma](../extensibility/how-to-use-text-markers.md)
