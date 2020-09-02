---
title: Kullanıcı ayarları desteği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 80734d9859df2e06bc51d40e1fffa40c7d97c7a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691807"
---
# <a name="support-for-user-settings"></a>Kullanıcı Ayarları için Destek
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage, bir Kullanıcı **Araçlar** menüsündeki **Içeri/dışarı aktarma ayarlarını** seçtiğinde devam eden durum değişkenlerinin grupları olan bir veya daha fazla ayar kategorisi tanımlayabilir. Bu kalıcılığı etkinleştirmek için içindeki ayarlar API 'Lerini kullanın [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 Özel ayar noktası olarak adlandırılan bir kayıt defteri girdisi ve bir GUID, VSPackage 'ın ayarlar kategorisini tanımlar. VSPackage, her biri özel bir ayar noktası tarafından tanımlanan birden çok ayarlar kategorisini destekleyebilir.  
  
- Birlikte çalışma derlemelerini temel alan ayarların uygulamaları ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> arabirimini kullanarak), kayıt defterini düzenleyerek veya bir kaydedici betiği (. rgs dosyası) kullanarak özel ayarlar noktası oluşturmanız gerekir. Daha fazla bilgi için bkz. [kaydedici betikleri oluşturma](https://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
- Yönetilen paket çerçevesini (MPF) kullanan kod, <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> her özel ayar noktası Için VSPackage öğesine ekleyerek özel ayar noktaları oluşturmaktır.  
  
     Tek bir VSPackage birkaç özel ayar noktasını destekliyorsa, her özel ayar noktası ayrı bir sınıf tarafından uygulanır ve her biri sınıfının benzersiz bir örneği tarafından kaydedilir <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Sonuç olarak, sınıf uygulayan bir ayar birden fazla ayar kategorisini destekleyebilir.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Özel ayarlar noktası kayıt defteri girdisi ayrıntıları  
 Özel ayar noktaları, aşağıdaki konumdaki bir kayıt defteri girişinde oluşturulur: HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings \\ `<CSPName>` , burada `<CSPName>` VSPackage 'ın desteklediği özel ayarlar noktasının adıdır ve *\<Version>* sürümüdür [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Örneğin, 8,0.  
  
> [!NOTE]
> \\ *\<Version>* [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tümleşik GELIŞTIRME ortamı (ıde) başlatıldığında HKEY_LOCAL_MACHINE \software\microsoft\visualstudio 'in kök yolu alternatif bir kökle geçersiz kılınabilir. Daha fazla bilgi için bkz. [komut satırı anahtarları](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Kayıt defteri girdisinin yapısı aşağıda gösterilmektedir:  
  
 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \Usersettings\  
  
 `<CSPName`>= s ' #12345 '  
  
 Paket = ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX} '  
  
 Kategori = ' {YYYYYY YYYY yyyy YYYY YYYYYYYYY} '  
  
 ResourcePackage = ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ} '  
  
 AlternateParent = CategoryName  
  
|Ad|Tür|Veriler|Description|  
|----------|----------|----------|-----------------|  
|(Varsayılan)|REG_SZ|Özel ayarlar noktasının adı|Anahtarın adı, `<CSPName`>, özel ayar noktasının yerelleştirilmemiş adıdır.<br /><br /> MPF tabanlı uygulamalar için, anahtarın adı, `categoryName` `objectName` oluşturucunun ve bağımsız değişkenlerinin içine birleştirilerek elde edilir <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `categoryName_objectName` .<br /><br /> Anahtar boş olabilir veya bir uydu DLL içindeki yerelleştirilmiş dizeye başvuru KIMLIĞINI içerebilir. Bu değer, `objectNameResourceID` bağımsız değişkenden <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> oluşturucuya alınır.|  
|Paket|REG_SZ|GUID|Özel ayarlar noktasını uygulayan VSPackage GUID 'SI.<br /><br /> MPF tabanlı uygulamalar <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sınıfını kullanarak, `objectType` <xref:System.Type> Bu değeri elde etmek Için VSPackage 'ın ve Reflection içeren bağımsız değişkenini kullanın.|  
|Kategori|REG_SZ|GUID|Ayarlar kategorisini tanımlayan GUID.<br /><br /> Birlikte çalışma derlemelerini temel alan uygulamalar için bu değer, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 'nin ve yöntemlerine geçirdiği rastgele seçilmiş BIR GUID olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> . Bu iki yöntemin tüm uygulamaları GUID bağımsız değişkenlerini doğrulamalıdır.<br /><br /> MPF tabanlı uygulamalar için, bu GUID, <xref:System.Type> Ayarlar mekanizmasını uygulayan sınıf tarafından alınır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .|  
|ResourcePackage|REG_SZ|GUID|İsteğe bağlı.<br /><br /> VSPackage uygulama bunları sağlayamadıysanız, yerelleştirilmiş dizeleri içeren uydu DLL yolu.<br /><br /> MPF doğru kaynak VSPackage 'ı almak için yansıma kullanır, bu nedenle <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sınıf bu bağımsız değişkeni belirtmiyor.|  
|AlternateParent|REG_SZ|Bu özel ayarlar noktasını içeren Araçlar Seçenekler sayfasının altındaki klasörün adı.|İsteğe bağlı.<br /><br /> Bu değeri yalnızca bir ayar uygulamasının, durumu kaydetmek için Otomasyon modelindeki mekanizmadan değil, Kalıcılık mekanizmasını kullanan **araç seçenekleri** sayfalarını desteklemesi gerekir [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .<br /><br /> Bu durumlarda, AlternateParent anahtarındaki değer, `topic` `topic.sub-topic` belirli bir **araçları seçenekler** sayfasını tanımlamak için kullanılan dizenin bölümüdür. Örneğin, **araçları seçenekler** sayfasında `"TextEditor.Basic"` AlternateParent değeri olacaktır `"TextEditor"` .<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>Özel ayarlar noktasını oluşturduğunda, kategori adı ile aynı olur.|
