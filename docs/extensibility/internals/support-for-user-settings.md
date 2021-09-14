---
title: Kullanıcı Desteği Ayarlar | Microsoft Docs
description: Visual Studio SDK'sı'nın ayarlar API'lerini kullanarak ayarlar kategorilerinin kalıcı Visual Studio öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626066"
---
# <a name="support-for-user-settings"></a>Kullanıcı Ayarları için Destek
VSPackage bir veya daha fazla ayar kategorisi tanımlayabilir. Bu kategoriler, kullanıcı  Araçlar menüsündeki İçeri/Dışarı Aktarma Ayarlar değişkenlerini seçtiklerinde kalıcı olan durum **değişkeni gruplarıdır.** Bu kalıcılığı etkinleştirmek için içinde ayarlar API'lerini [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] kullanırsiniz.

 Özel Ayarlar Noktası olarak adlandırılan bir kayıt defteri girişi ve GUID, VSPackage'ın ayarlar kategorisini tanımlar. VSPackage, her biri özel bir Ayarlar Noktası tarafından tanımlanan birden çok ayar kategorilerini destekleyene.

- Birlikte çalışma derlemelerini (arabirimi kullanarak) temel alan ayarların uygulamaları, kayıt defterini düzenleyerek veya bir Kayıt Şirketi betiği (.rgs dosyası) kullanarak Özel Ayarlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> Noktası oluşturmalı. Daha fazla bilgi için [bkz. Kayıt Şirketi Betikleri Oluşturma.](/cpp/atl/creating-registrar-scripts)

- Yönetilen Paket Çerçevesi (MPF) kullanan kod, her özel Ayarlar Noktası için VSPackage'a bir ekerek Özel Ayarlar <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Noktası oluşturmalı.

     Tek bir VSPackage birkaç Özel Ayarlar Noktasını destekliyorsa, her özel Ayarlar Noktası ayrı bir sınıf tarafından uygulanır ve her biri sınıfın benzersiz bir örneği tarafından <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> kaydedilir. Sonuç olarak, sınıf uygulayan bir ayar birden fazla ayar kategorisini destekleyene.

## <a name="custom-settings-point-registry-entry-details"></a>Özel Ayarlar Noktası Kayıt Defteri Giriş Ayrıntıları
 Özel Ayarlar Noktaları şu konumdaki bir kayıt defteri girdisinde oluşturulur: HKLM\Software\Microsoft\VisualStudio \UserSettings , burada VSPackage'ın desteklediği Özel Ayarlar Noktasının adıdır ve sürümüdür, örneğin \\ *\<Version>* \\ `<CSPName>` `<CSPName>` *\<Version>* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8.0.

> [!NOTE]
> Tümleşik geliştirme ortamı (IDE) HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudiokök yolu alternatif bir \\ *\<Version>* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kökle geçersiz kılınabilir. Daha fazla bilgi için [bkz. Komut Satırı Anahtarları.](../../extensibility/command-line-switches-visual-studio-sdk.md)

 Kayıt defteri girişinin yapısı aşağıda gösterilmiştir:

 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings\

 `<CSPName`>= '#12345'

 Paket = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'

 Kategori = '{YYYYY YYYY YYYY YYYYYYYY}'

 ResourcePackage = '{ZZZZZZ ZZ ZZ ZZ ZZZZ ZZZZZZZ}'

 AlternateParent = CategoryName

| Ad | Tür | Veriler | Description |
|-----------------|--------| - | - |
| (Varsayılan) | REG_SZ | Özel Ayarlar Noktası adı | Anahtarın adı olan>, Özel Ayarlar `<CSPName` Noktası'nın yerel olmayan adıdır.<br /><br /> MPF'yi temel alan uygulamalar için anahtarın adı, oluşturucus un ve bağımsız değişkenleri `categoryName` `objectName` ile <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> birleştirerek elde `categoryName_objectName` edilir.<br /><br /> Anahtar boş olabilir veya bir uydu DLL'deki yerelleştirilmiş dizenin başvuru kimliğini içerebilir. Bu değer, bağımsız değişkenden `objectNameResourceID` oluşturucuya <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> elde edilir. |
| Paket | REG_SZ | GUID | Özel Ayarlar Noktası uygulayan VSPackage GUID'i.<br /><br /> sınıfını kullanarak MPF'yi temel alan uygulamalar, bu değeri elde etmek için VSPackage'ın ve yansımanın bulunduğu oluşturucu <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `objectType` bağımsız <xref:System.Type> değişkenlerini kullanır. |
| Kategori | REG_SZ | GUID | Ayarlar kategorisini tanımlayan GUID.<br /><br /> Birlikte çalışma derlemelerini temel alan uygulamalar için, bu değer IDE'nin ve yöntemlerine geçtiği rastgele seçilen bir GUID [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> olabilir. Bu iki yöntemin tüm uygulamaları GUID bağımsız değişkenlerini doğrulamalı.<br /><br /> MPF'yi temel alan uygulamalar için bu GUID, ayarlar <xref:System.Type> mekanizmasını uygulayan sınıfının tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elde edilir. |
| ResourcePackage | REG_SZ | GUID | İsteğe bağlı.<br /><br /> Uygulama VSPackage tarafından yoksa, yerelleştirilmiş dizeleri içeren uydu DLL'nin yolu.<br /><br /> MPF, doğru kaynak VSPackage'ını almak için yansıma kullanır, bu nedenle <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sınıf bu bağımsız değişkeni ayarlamaz. |
| AlternateParent | REG_SZ | Bu Özel Uygulama Noktası'nın bulunduğu Araçlar Seçenekleri sayfasının altındaki klasörün Ayarlar. | İsteğe bağlı.<br /><br /> Bu değeri yalnızca ayarlar uygulaması,  durumu kaydetmek için otomasyon modelinde kullanılan mekanizma yerine içinde kalıcılık mekanizmasını kullanan Araçlar Seçenekleri [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sayfalarını destekliyorsa ayarlayabilirsiniz.<br /><br /> Bu durumlarda AlternateParent anahtarında yer alan değer, belirli `topic` `topic.sub-topic` **ToolsOptions** sayfasını tanımlamak için kullanılan dizenin bölümü olur. Örneğin **AraçlarSeçenekler sayfasında** `"TextEditor.Basic"` AlternateParent değeri `"TextEditor"` olur.<br /><br /> Özel <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Uygulama Noktası Ayarlar, kategori adıyla aynıdır. |
