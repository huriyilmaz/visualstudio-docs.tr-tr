---
title: Kullanıcı Ayarları desteği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704784"
---
# <a name="support-for-user-settings"></a>Kullanıcı Ayarları için Destek
VSPackage, bir kullanıcı **Araçlar** menüsündeki **İçe/Dışa Aktar Ayarları** komutunu seçtiğinde devam eden durum değişkenleri grupları olan bir veya daha fazla ayar kategorisi tanımlayabilir. Bu kalıcılığı etkinleştirmek için, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]'deki ayarlar API'lerini kullanırsınız.

 Özel Ayarlar Noktası ve GUID olarak adlandırılan bir kayıt defteri girişi, VSPackage'ın ayarlar kategorisini tanımlar. VSPackage, her biri Özel Ayarlar Noktası tarafından tanımlanan birden çok ayar kategorilerini destekleyebilir.

- Interop derlemelerine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> (arabirimi kullanarak) dayalı ayarların uygulamaları, kayıt defterini düzenleyerek veya Kayıt Defteri komut dosyası (.rgs dosyası) kullanarak Özel Ayarlar Noktası oluşturmalıdır. Daha fazla bilgi için [Bkz. Kayıt Defteri Komut Dosyaları Oluşturma.](/cpp/atl/creating-registrar-scripts)

- Yönetilen Paket Çerçevesi'ni (MPF) kullanan kod, her <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Özel Ayarlar Noktası için VSPackage'a bir tane ekleyerek Özel Ayarlar Noktaları oluşturmalıdır.

     Tek bir VSPackage birkaç Özel Ayar Noktası'nı destekliyorsa, her Özel Ayarlar Noktası ayrı bir <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sınıf tarafından uygulanır ve her biri sınıfın benzersiz bir örneği tarafından kaydedilir. Sonuç olarak, bir ayar uygulayıcı sınıf birden fazla ayar kategorisini destekleyebilir.

## <a name="custom-settings-point-registry-entry-details"></a>Özel Ayarlar Nokta Kayıt Defteri Giriş Bilgileri
 Özel Ayarlar Noktaları aşağıdaki konumda bir kayıt defteri girişinde oluşturulur: HKLM\Software\Microsoft\VisualStudio\\*\< * `<CSPName>` Sürüm>\UserSettings\\`<CSPName>`, Özel Ayarlar Noktası'nın adı VSPackage destekler ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] * \<Sürüm>* sürümü , örneğin 8.0.

> [!NOTE]
> tümleşik geliştirme ortamı (IDE)\\başlattığında, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*\<Sürüm>* kök yolu alternatif bir kökle geçersiz kılınabilir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Daha fazla bilgi için [Komut Satırı Anahtarları'na](../../extensibility/command-line-switches-visual-studio-sdk.md)bakın.

 Kayıt defteri girişinin yapısı aşağıda gösterilmiştir:

 HKLM\Yazılım\Microsoft\VisualStudio\\*\<Sürüm>* \UserSettings\

 `<CSPName`>= '#12345'

 Paket = '{XXXXXX XXXX XXXX XXXX XXXXXXXXXXXX}'

 Kategori = '{YYYYYY YYYY YYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY}'

 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZZZZZZZZZZZZZ}'

 AlternativeParent = CategoryName

| Adı | Tür | Veriler | Açıklama |
|-----------------|--------| - | - |
| (Varsayılan) | REG_SZ | Özel Ayarlar Noktasının Adı | Anahtarın adı, `<CSPName`>, Özel Ayarlar Noktası'nın yerelleştirilmemiş adıdır.<br /><br /> MPF'ye dayalı uygulamalariçin, `categoryName` anahtarın `objectName` <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> adı, oluşturucunun bağımsız değişkenlerini `categoryName_objectName`.<br /><br /> Anahtar boş olabilir veya bir uydu DLL'de yerelleştirilmiş dize için başvuru kimliği içerebilir. Bu değer `objectNameResourceID` bağımsız değişkenden <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> oluşturucuya elde edilir. |
| Paket | REG_SZ | GUID | Özel Ayarlar Noktası'nı uygulayan VSPackage'ın GUID'i.<br /><br /> Sınıfı kullanarak MPF'ye dayalı uygulamalar, bu `objectType` değeri elde etmek için <xref:System.Type> VSPackage'ın ve yansımanın bulunduğu kurucu bağımsız değişkenini kullanır. <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> |
| Kategori | REG_SZ | GUID | Ayarlar kategorisini tanımlayan GUID.<br /><br /> Interop derlemelerine dayalı uygulamalar için bu değer, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE'nin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> yöntemlere geçtiği rasgele seçilmiş bir GUID olabilir. Bu iki yöntemin tüm uygulamaları, GUID bağımsız değişkenlerini doğrulamalıdır.<br /><br /> MPF'ye dayalı uygulamalar için bu GUID, <xref:System.Type> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayarlar mekanizmasını uygulayan sınıfın tarafından elde edilir. |
| Kaynak Paketi | REG_SZ | GUID | İsteğe bağlı.<br /><br /> Uygulayan VSPackage bunları sağlamazsa, yerelleştirilmiş dizeleri içeren uydu DLL yolu.<br /><br /> MPF doğru kaynak VSPackage elde etmek <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> için yansıma kullanır, böylece sınıf bu bağımsız değişkeni ayarlamaz. |
| Alternatif Ebeveyn | REG_SZ | Bu Özel Ayarlar Noktası'nı içeren Araçlar Seçenekleri sayfasının altındaki klasörün adı. | İsteğe bağlı.<br /><br /> Bu değeri yalnızca bir ayar uygulaması, durumu kaydetmek için otomasyon modelindeki mekanizma [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] yerine kalıcılık mekanizmasını kullanan Araçlar **Seçenekleri** sayfalarını destekliyorsa ayarlamanız gerekir.<br /><br /> Bu gibi durumlarda, Alternatif Ebeveyn anahtarındaki `topic` değer, `topic.sub-topic` belirli **ToolsOptions** sayfasını tanımlamak için kullanılan dize bölümüdür. Örneğin, **ToolsOptions** sayfası `"TextEditor.Basic"` için AlternateParent değeri `"TextEditor"`.<br /><br /> Özel <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Ayarlar Noktası'nı oluşturduğunda, kategori adı ile aynıdır. |
