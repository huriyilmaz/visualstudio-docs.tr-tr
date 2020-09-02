---
title: Özel kategoriler uygulama ve öğeleri görüntüleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796831"
---
# <a name="implementing-custom-categories-and-display-items"></a>Özel Kategoriler ve Görüntüleme Öğeleri Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] özel kategoriler ve görüntüleme öğeleri aracılığıyla tümleşik geliştirme ortamı (IDE) için yazı tiplerinin ve renklerin, metin ve renklerinin denetimini sağlayabilir.  
  
 Özel kategoriler ve görüntüleme öğeleri, **yazı tipleri ve renkler** Özellik sayfaınlardır. **Yazı tipleri ve renkler** özellik sayfasını açmak Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Ortamı** genişletin ve ardından **yazı tipleri ve renkler**' e tıklayın.  
  
 Bu mekanizma kullanılırken, VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> arabirimini ve ilişkili arabirimlerini uygulamalıdır.  
  
 Bu mekanizma, var olan tüm **görüntüleme öğelerini** ve bunları içeren **kategorileri** değiştirmek için kullanılabilir. Ancak, **metin EditorCategory** veya **görüntüleme öğelerini**değiştirmek için kullanılmamalıdır. Daha fazla bilgi için bkz. [yazı tipi ve renge genel bakış](../extensibility/font-and-color-overview.md).  
  
 Özel **Kategoriler** uygulamak veya **öğeleri göstermek**Için bir VSPackage gerekir:  
  
- Kayıt defterinde kategoriler oluşturun veya bunları tespit edin.  
  
   IDE 'nin **yazı tipleri ve renkler** Özellik sayfasının uygulanması, belirli bir kategoriyi destekleyen hizmeti doğru şekilde sorgulamak için bu bilgileri kullanır.  
  
- Kayıt defterinde gruplar oluşturun veya (isteğe bağlı).  
  
   İki veya daha fazla kategorinin birleşimini temsil eden bir grup tanımlamak faydalı olabilir. Bir grup tanımlanmışsa, IDE otomatik olarak alt kategorileri birleştirir ve görüntüleme öğelerini grup içinde dağıtır.  
  
- IDE desteği uygulayın.  
  
- Yazı tipi ve renk değişikliklerini işleyin.  
  
  Daha fazla bilgi için bkz. [depolanan yazı tipine ve renk ayarlarına erişme](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Kategori oluşturmak veya tanımlamak için  
  
- [HKLM\SOFTWARE\Microsoft \Adim \\ *\<Visual Studio version>* \Fontandcolors \\ `<Category>` ] altında Kategori kayıt defteri girdisinin özel bir türünü oluşturun  
  
   *\<Category>* kategorinin yerelleştirilmemiş adıdır.  
  
- Kayıt defterini iki değerle doldurun:  
  
  |Ad|Tür|Veriler|Description|  
  |----------|----------|----------|-----------------|  
  |Kategori|REG_SZ|GUID|Kategoriyi tanımlamak için oluşturulmuş bir GUID.|  
  |Paket|REG_SZ|GUID|Kategoriyi destekleyen VSPackage hizmetinin GUID 'SI.|  
  
  Kayıt defterinde belirtilen hizmetin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> karşılık gelen kategori için bir uygulamasını sağlaması gerekir.  
  
## <a name="to-create-or-identify-groups"></a>Grupları oluşturmak veya tanımlamak için  
  
- [HKLM\SOFTWARE\Microsoft \Adim \\ *\<Visual Studio version>* \Fontandcolors \\ *\<group>* ] altında Kategori kayıt defteri girdisinin özel bir türünü oluşturun  
  
   *\<group>* grubun yerelleştirilmemiş adıdır.  
  
- Kayıt defterini iki değerle doldurun:  
  
  |Ad|Tür|Veriler|Description|  
  |----------|----------|----------|-----------------|  
  |Kategori|REG_SZ|GUID|Grubu tanımlamak için oluşturulmuş bir GUID.|  
  |Paket|REG_SZ|GUID|Kategoriyi destekleyen hizmetin GUID 'SI.|  
  
  Kayıt defterinde belirtilen hizmetin, `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` karşılık gelen grup için bir uygulamasını sağlaması gerekir.  
  
## <a name="to-implement-ide-support"></a>IDE desteğini uygulamak için  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` Belirtilen her bir **Kategori** veya grup GUID 'si için bir arabirim ya da bir arabirim döndüren uygulayın.  
  
- Desteklediği her **Kategori** Için, VSPackage arabirimin ayrı bir örneğini uygular <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> .  
  
- İle uygulanan yöntemler <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , Ile IDE sağlamalıdır:  
  
  - Kategorideki **görüntüleme öğelerinin** listesi **.**  
  
  - **Görüntüleme öğeleri**için yerelleştirilebilir adlar.  
  
  - **Kategorinin**her üyesi için bilgi görüntüler.  
  
  > [!NOTE]
  > Her **Kategori** en az bir **görüntüleme öğesi**içermelidir.  
  
- IDE, `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` birkaç kategorinin birleşimini tanımlamak için arabirimini kullanır.  
  
   Uygulama, IDE 'yi şunları sağlar:  
  
  - Belirli bir grubu oluşturan **kategorilerin** bir listesi.  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>Grup içindeki her **kategoriyi** destekleme örneklerine erişin.  
  
  - Yerelleştirilebilir grup adları.  
  
- IDE 'yi güncelleştirme:  
  
   IDE, **yazı tipi ve renk** ayarları hakkındaki bilgileri önbelleğe alır. Bu nedenle, IDE **yazı tipi ve renk** yapılandırmasının herhangi bir değişikliği yapıldıktan sonra önbelleğin güncel olduğundan emin olmak önerilir.  
  
  Önbelleğin güncelleştirilmesi arabirim aracılığıyla yapılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> ve küresel olarak veya yalnızca seçili öğeler üzerinde gerçekleştirilebilir.  
  
## <a name="to-handle-font-and-color-changes"></a>Yazı tipi ve renk değişikliklerini Işlemek için  
 VSPackage 'ın görüntülediği metnin renklendirmesi düzgün şekilde desteklemek için, VSPackage 'ı destekleyen renklendirme hizmeti, **yazı tipleri ve renkler** Özellikler sayfasından yapılan Kullanıcı tarafından başlatılan değişikliklere yanıt vermelidir. Bir VSPackage bunu şu şekilde yapar:  
  
- Arabirimi uygulayarak IDE tarafından oluşturulan olayları işleme <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> .  
  
     IDE, **yazı tipleri ve renkler** sayfasındaki Kullanıcı değişikliklerinin ardından uygun yöntemi çağırır. Örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> Yeni bir yazı tipi seçilirse yöntemini çağırır.  
  
     -veya-  
  
- IDE, değişiklikler için yoklanıyor.  
  
     Bu, sistem tarafından uygulanan arabirim aracılığıyla yapılabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Birincil olarak kalıcılık desteği için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> yöntemi **görüntüleme öğeleri**için yazı tipi ve renk bilgilerini almak üzere kullanılabilir. Daha fazla bilgi için bkz. [depolanan yazı tipine ve renk ayarlarına erişme](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    > Yoklamayla elde edilen sonuçların doğru olduğundan emin olmak için, arabirimin <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> alma yöntemleri çağrılmadan önce bir önbellek temizleme ve güncelleştirme gerekip gerekmediğini anlamak için arabirimi kullanmak yararlı olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Metin renklendirme için yazı tipi ve renk bilgileri alma](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Depolanan yazı tipine ve renk ayarlarına erişme](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Nasıl yapılır: yerleşik yazı tiplerine ve renk şemasına erişme](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Yazı Tipi ve Renklere Genel Bakış](../extensibility/font-and-color-overview.md)
