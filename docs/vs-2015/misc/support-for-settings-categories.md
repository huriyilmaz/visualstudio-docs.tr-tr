---
title: Ayarlar kategorileri için destek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: jillfra
ms.openlocfilehash: 15a3896f8a2010a063393d3a11c1ed3453a008d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689094"
---
# <a name="support-for-settings-categories"></a>Ayarlar kategorileri için destek
Bir ayarlar kategorisi, tümleşik geliştirme ortamını (IDE) özelleştiren bir seçenek grubundan oluşur. Örneğin, ayarlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pencerelerin yerleşimini ve menülerin içeriğini denetleyebilir. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Ayarları içeri ve dışarı aktarma Sihirbazı 'nı**başlatmak için **Araçlar** menüsünde **içeri ve dışarı aktarma ayarları** ' na tıklayın. Sihirbaz üç seçenek sunar: ayarlarınızı dışarı aktarın, içeri aktarın veya sıfırlayın. Örneğin, dışarı aktar seçildiğinde, sihirbazın **dışarı aktarılacak ayarları seçin** sayfası açılır.  
  
 Bu sayfanın gezinti bölmesindeki ağaç denetimi kategorileri listeler. Kategori bir "özel ayarlar noktası", yani bir onay kutusu olarak görünen ilgili ayarları grubudur. Bir. Vsettings dosyasında kalıcı olacak kategorileri seçmek için bu onay kutularını kullanın. Sihirbaz. Vsettings dosyasını adınızla yolunu belirtmenizi sağlar.  
  
> [!NOTE]
> Ayarlar bir kategori olarak kaydedilir veya geri yüklenir ve bağımsız ayar adları sihirbazda görüntülenmez.  
  
 Yönetilen paket çerçevesi (MPF), en az ek kodla ayar kategorilerinin oluşturulmasını destekler.  
  
- Sınıfına göre kategori için bir kapsayıcı sağlamak üzere VSPackage oluşturun altsınıflama <xref:Microsoft.VisualStudio.Shell.Package> .  
  
- Kategorinin kendisini sınıfından türeterek oluşturabilirsiniz <xref:Microsoft.VisualStudio.Shell.DialogPage> .  
  
- İle ikisini ile bağlanırsınız <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .  
  
## <a name="support-for-settings-categories"></a>Ayarlar kategorileri için destek  
 <xref:Microsoft.VisualStudio.Shell.Package>Sınıfı, kategori oluşturma desteği sağlar. <xref:Microsoft.VisualStudio.Shell.DialogPage>Sınıfı bir kategori uygular. Varsayılan uygulamasının, <xref:Microsoft.VisualStudio.Shell.DialogPage> genel özelliklerini bir kategori olarak bir kullanıcıya sunar. Daha fazla bilgi için bkz. [ayar kategorisi oluşturma](../extensibility/creating-a-settings-category.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>Sınıfı <xref:Microsoft.VisualStudio.Shell.IProfileManager> , her iki seçenek sayfası ve Kullanıcı ayarı için kalıcılık sağlayan öğesini uygular. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>Ve <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> yöntemleri, ayarlarını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sırasıyla veya olarak sağlayan bir. vssettings dosyasına kalıcı hale <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> getirir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> . <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A>Yöntemi ayarları varsayılan değerlerine sıfırlar.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>Sınıfı, <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> XML akışından ad-değer çiftlerini okuyan yönteminin bir uygulamasını sağlar ve türetilmiş sınıftaki ortak özellikleri bulmaya yönelik yansımayı kullanır <xref:Microsoft.VisualStudio.Shell.DialogPage> . Ad-değer çiftleriyle eşleşen adlara sahip özelliklere karşılık gelen değerler verilir.  
  
 Varsayılan uygulamasının, <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> türetilmiş sınıftaki ortak özellikleri bulması için yansıma kullanır <xref:Microsoft.VisualStudio.Shell.DialogPage> ve özellik adlarını ve değerlerini ad-değer ÇIFTLERI olarak XML akışına yazar.  
  
### <a name="settings-category-registry-path"></a>Ayarlar kategorisi kayıt defteri yolu  
 Ayarlar kategorisinin kayıt defteri yolu <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> ,, sözcük, Kullanıcı ayarları, Ayarlar kategorisi ve özel ayar noktasının adı birleştirilerek belirlenir. Ayarlar kategorisi ve özel ayar noktası adları, kayıt defterinde görüntülenen kurallı, yerelleştirilmemiş adı biçimlendirmek için bir alt çizgiyle birleştirilir ve ayrılır. Örneğin, Ayarlar kategorisi "kategorim", özel ayarlar noktası adı "ayarlarım" ve ApplicationRegistryRoot HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp ise, ayarlar kategorisinin kayıt defteri anahtarı HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My ayarları vardır.  
  
> [!NOTE]
> Kurallı ad, bir kullanıcı arabiriminde (UI) görünmez. Okunabilir bir adı, programlı tanımlayıcı (ProgID) gibi ayarlar kategorisiyle ilişkilendirmek için kullanılır.  
  
### <a name="settings-category-attribute"></a>Ayarlar kategorisi özniteliği  
 , <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Kategoriyi sağlayan VSPackage ile bir kategoriyi Ilişkilendirerek **Içeri ve dışarı aktarma Sihirbazı** ' nda özel ayar noktalarına kategorilerin eşlenmesini belirler. Aşağıdaki kod parçasını göz önünde bulundurun:  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 Kaynak KIMLIĞI 106 "My Category", 107 "My Settings" ve 108 "çeşitli seçenekler" ile eşlenir. Bu `MyPackage` , Category_My ayarlarımı sağlayan bu olduğunu bildirir. Kategori, `OptionsPageGeneral` uygulanması gereken sınıf tarafından sağlanır <xref:Microsoft.VisualStudio.Shell.IProfileManager> . Bu kategorideki ayarlar, sınıfının ortak özellikleridir `OptionsPageGeneral` .  
  
 Ayarları **içeri ve dışarı aktarma sihirbazında**, ayarlar noktasının adı, ayarlarım vardır. Ayarlar noktası seçildiğinde, açıklama, **çeşitli seçenekler**görüntülenir. Ayarlar noktası adı ve açıklaması, yerelleştirilmiş dize kaynaklarından alınır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seçenekler sayfası oluşturma](../extensibility/creating-an-options-page.md)   
 [VSSDK örnekleri](../misc/vssdk-samples.md)   
 [VSPackage durumu](../misc/vspackage-state.md)   
 [Visual Studio 'da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)