---
title: Yazı tipi ve renge genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204352"
---
# <a name="font-and-color-overview"></a>Yazı Tipi ve Renklere Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tümleşik geliştirme ortamındaki (IDE) metin yazı tipi ve renk ayarları ele alınmaktadır. Ayrıca, kategorilerin ve görüntüleme öğelerinin kavramlarını tanıtır ve VSPackages ve çekirdek düzenleyicisinin metin özniteliklerini nasıl kullandığını açıklar.  
  
## <a name="the-fonts-and-colors-property-page"></a>Yazı tipleri ve renkler Özellik sayfası  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Yazı tipleri ve renkler** Özellik sayfasında, tümleşik GELIŞTIRME ortamında (IDE), görünen metnin özniteliklerini yönetebilirsiniz. **Yazı tipleri ve renkler** özellik sayfasını bulmak Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Ortam**' ı genişletin ve ardından **yazı tipleri ve renkler**' e tıklayın.  
  
## <a name="categories-and-display-items"></a>Kategoriler ve görüntüleme öğeleri  
 Yazı tipleri ve renkler **Kategoriler** halinde düzenlenir ve **öğeleri görüntüler**.  
  
- **Kategori** , bir dizi **görüntü öğesi**için mantıksal veya işlevsel bir kapsayıcıdır.  
  
   **Kategorilerin** listesi, **yazı tipleri ve renkler** Özellik sayfasının açılan **ayarlarını göster** kutusunda bulunur.  
  
- Bir **görüntüleme öğesi** , bir yorum, bir dize veya görüntülenirken renklendirilmek üzere bir denetim yapısı gibi iyi tanımlanmış bir metin varlıktır.  
  
  Her bir **görüntüleme öğesi** , kendisini içeren **Kategori** içinde benzersiz bir şekilde tanımlanır. Sonuç olarak, birden fazla **Kategori** aynı ada sahip bir **görüntüleme öğesine** sahip olabilir.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Yazı tiplerinin ve renklerin VSPackage denetimi  
 , [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] VSPackages 'ın şunları yapmasına izin verir:  
  
- Yazı tipi ve renk **kategorilerini**tanımlayın.  
  
- **Görüntü öğelerini**sunmak için kullanılan yazı tiplerini ve renkleri belirtin.  
  
- **Yazı tipleri ve renkler** Özellik sayfasıyla etkileşime geçin.  
  
- Birden çok **kategoriyi** gruplar halinde toplar.  
  
- Değişiklikleri varsayılan ayarlarda kalıcı hale getirin.  
  
  İçindeki yazı tipi ve renk seçimleriyle etkileşimde bulunmak için iki yol vardır [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- Bir yol *Sözdizimi renklendirmesi*olarak adlandırılır. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Bir dil hizmetini uygulamak ve bir kaynak Düzenleyicisi oluşturmak için var olan düzenleyiciyi özelleştiren VSPackage tarafından kullanılır.  
  
   Bu mekanizmayı yalnızca bir **Kategori** destekler, yani **metin düzenleyici**.  
  
- Daha genel bir alternatif, metin görüntülenirken kaynak Düzenleyicisi dışındaki diğer tüm **kategorileri** ve Kullanıcı Arabirimi bileşenlerini destekler. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Çekirdek Düzenleyicisi metin ayarları  
 Bir dil hizmeti nesnesinin temel düzenleyicisinin yazı tipi ve renk ayarları, **yazı tipleri ve renkler** Özellik sayfasının açılan **ayarlarını göster** kutusunda bulunan **metin editorcategory** öğesine tabidir.  
  
 Düzenleyicilerle çalışırken, dil hizmetinin **metin Düzenleyicisi** ayarlarını denetlemek ve genişletmek için sağladığı özel yazı tipi ve renk denetim mekanizmasını kullanmanız gerekir. Mekanizmaya *sözdizimi renklendirme* adı verilir ve şunları sağlar:  
  
- Görüntüleme öğelerinin yazı tiplerini ve renklerini yönetmek için basitleştirilmiş bir tekniktir.  
  
   Daha fazla bilgi için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> bölümlerine bakın.  
  
- İyi tanımlanmış ve iyileştirilmiş bir renklendirme mekanizması.  
  
   Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- Her ikisinin de **metin düzenleyici kategorisinden** yerleşik görüntü öğelerini kullanma ve bunları genişletme özelliği.  
  
   Daha fazla bilgi için bkz. [nasıl yapılır: yerleşik Renklenebilir öğeler](../extensibility/internals/how-to-use-built-in-colorable-items.md) ve [özel Renklenebilir öğeler](../extensibility/internals/custom-colorable-items.md)kullanma.  
  
- **Metin düzenleyici** kategorisiyle hem yerleşik hem de özel görüntüleme öğelerinin geçerli durumunun otomatik kalıcılığı.  
  
  Sözdizimi renklendirme hakkında daha fazla bilgi için bkz. [eski dil hizmetinde söz dizimi renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenleyicideki eski arabirimler](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
