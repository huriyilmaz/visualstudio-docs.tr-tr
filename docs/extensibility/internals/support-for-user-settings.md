---
title: kullanıcı Ayarlar için destek | Microsoft Docs
description: Visual Studio SDK 'daki ayarlar apı 'lerini kullanarak ayarlar kategorilerinin kalıcılığını nasıl etkinleştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d317809bde56132f990c11e641ae151fcbac8eff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086514"
---
# <a name="support-for-user-settings"></a>Kullanıcı Ayarları için Destek
bir vspackage, bir kullanıcı **araçlar** menüsünde **İçeri/Dışarı Aktarma Ayarlar** komutunu seçtiğinde devam eden durum değişkenlerinin grupları olan bir veya daha fazla ayar kategorisi tanımlayabilir. Bu kalıcılığı etkinleştirmek için içindeki ayarlar API 'Lerini kullanın [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 özel Ayarlar noktası ve guıd olarak adlandırılan bir kayıt defteri girişi vspackage 'ın ayarlar kategorisini tanımlar. vspackage, her biri özel bir Ayarlar noktası tarafından tanımlanan birden çok ayarlar kategorisini destekleyebilir.

- birlikte çalışma derlemelerini temel alan ayarların uygulamaları ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> arabirimini kullanarak), kayıt defterini düzenleyerek veya bir kaydedici betiği (. rgs dosyası) kullanarak özel Ayarlar noktası oluşturmanız gerekir. Daha fazla bilgi için bkz. [kaydedici betikleri oluşturma](/cpp/atl/creating-registrar-scripts).

- yönetilen paket çerçevesini (mpf) kullanan kod <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> , her özel Ayarlar noktası için vspackage öğesine ekleyerek özel Ayarlar noktaları oluşturmaktır.

     tek bir vspackage birkaç özel Ayarlar noktasını destekliyorsa, her özel Ayarlar noktası ayrı bir sınıf tarafından uygulanır ve her biri sınıfının benzersiz bir örneği tarafından kaydedilir <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Sonuç olarak, sınıf uygulayan bir ayar birden fazla ayar kategorisini destekleyebilir.

## <a name="custom-settings-point-registry-entry-details"></a>özel Ayarlar noktası kayıt defteri girdisi ayrıntıları
 özel Ayarlar noktaları, aşağıdaki konumdaki bir kayıt defteri girişinde oluşturulur: hklm\software\microsoft\visualstudio \\ *\<Version>* \usersettings \\ `<CSPName>` , burada `<CSPName>` vspackage 'ın desteklediği özel Ayarlar noktasının adı ve *\<Version>* sürümüdür [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . örneğin, 8,0.

> [!NOTE]
> \\ *\<Version>* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik GELIŞTIRME ortamı (ıde) başlatıldığında HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudiokök yolu alternatif bir kökle geçersiz kılınabilir. Daha fazla bilgi için bkz. [komut satırı anahtarları](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Kayıt defteri girdisinin yapısı aşağıda gösterilmektedir:

 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \Usersettings\

 `<CSPName`>= s ' #12345 '

 Paket = ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX} '

 Kategori = ' {YYYYYY YYYY yyyy YYYY YYYYYYYYY} '

 ResourcePackage = ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ} '

 AlternateParent = CategoryName

| Ad | Tür | Veriler | Açıklama |
|-----------------|--------| - | - |
| (Varsayılan) | REG_SZ | özel Ayarlar noktasının adı | anahtarın adı `<CSPName`>, özel Ayarlar noktasının yerelleştirilmemiş adıdır.<br /><br /> MPF tabanlı uygulamalar için, anahtarın adı, `categoryName` `objectName` oluşturucunun ve bağımsız değişkenlerinin içine birleştirilerek elde edilir <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `categoryName_objectName` .<br /><br /> Anahtar boş olabilir veya bir uydu DLL içindeki yerelleştirilmiş dizeye başvuru KIMLIĞINI içerebilir. Bu değer, `objectNameResourceID` bağımsız değişkenden <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> oluşturucuya alınır. |
| Paket | REG_SZ | GUID | özel Ayarlar noktasını uygulayan vspackage guıd 'i.<br /><br /> MPF tabanlı uygulamalar <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sınıfını kullanarak, `objectType` <xref:System.Type> Bu değeri elde etmek Için VSPackage 'ın ve Reflection içeren bağımsız değişkenini kullanın. |
| Kategori | REG_SZ | GUID | Ayarlar kategorisini tanımlayan GUID.<br /><br /> Birlikte çalışma derlemelerini temel alan uygulamalar için bu değer, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 'nin ve yöntemlerine geçirdiği rastgele seçilmiş BIR GUID olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> . Bu iki yöntemin tüm uygulamaları GUID bağımsız değişkenlerini doğrulamalıdır.<br /><br /> MPF tabanlı uygulamalar için, bu GUID, <xref:System.Type> Ayarlar mekanizmasını uygulayan sınıf tarafından alınır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| ResourcePackage | REG_SZ | GUID | İsteğe bağlı.<br /><br /> VSPackage uygulama bunları sağlayamadıysanız, yerelleştirilmiş dizeleri içeren uydu DLL yolu.<br /><br /> MPF doğru kaynak VSPackage 'ı almak için yansıma kullanır, bu nedenle <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sınıf bu bağımsız değişkeni belirtmiyor. |
| AlternateParent | REG_SZ | bu özel Ayarlar noktasını içeren araçlar seçenekler sayfasının altındaki klasörün adı. | İsteğe bağlı.<br /><br /> Bu değeri yalnızca bir ayar uygulamasının, durumu kaydetmek için Otomasyon modelindeki mekanizmadan değil, Kalıcılık mekanizmasını kullanan **araç seçenekleri** sayfalarını desteklemesi gerekir [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .<br /><br /> Bu durumlarda, AlternateParent anahtarındaki değer, `topic` `topic.sub-topic` belirli bir **araçları seçenekler** sayfasını tanımlamak için kullanılan dizenin bölümüdür. Örneğin, **araçları seçenekler** sayfasında `"TextEditor.Basic"` AlternateParent değeri olacaktır `"TextEditor"` .<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>özel Ayarlar noktası oluşturduğunda, kategori adı ile aynı olur. |
