---
title: Özellikleri genişletme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690991"
---
# <a name="extending-properties"></a>Özellikleri Genişletme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Özellikler** penceresi, com ve com+ bileşenleri için bir evrensel Özellik tarayıcısıdır ve tüm [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ürünleri destekler. **Özellikler** penceresi, `ITypeInfo` Tümleşik GELIŞTIRME ortamındaki (IDE) diğer herhangi bir pencerede seçili olan nesnenin tasarım zamanı özelliklerini listelemek için tür bilgileri ve com+ meta verileri ile birlikte kullanılabilir.  
  
 Klavyede F4 tuşuna basılarak veya **Görünüm** menüsündeki **Özellikler penceresini** seçerek açılabilen **Özellikler** penceresi, yapılandırma bağımsız, tasarım zamanı özelliklerini ve seçili nesnelerin olaylarını görüntülemek ve düzenlemek için kullanılır. Çözümlerle ve projelerle ilişkili yapılandırma bağımlı özellikler, [özellik sayfalarında](../../extensibility/internals/property-pages.md)görüntülenir. Daha fazla bilgi için bkz. [nib: proje özellikleri](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md)ve [nib: projelerde öğe yönetimi](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Özellikler Penceresine Genel Bakış](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Özellik penceresi  
  
 Bu bölümde, **Özellikler** penceresinin bireysel alanlarıyla ilgili ayrıntılı bilgiler ve pencereyi doldurmak için uygulamanız ve çağırmanız gereken arabirimler yer almaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Özellikler Penceresine Genel Bakış](../../extensibility/internals/properties-window-overview.md)  
 Araç penceresi ve belge penceresine göre **Özellikler** penceresinin amacını açıklar.  
  
 [Şablon İlkesi ve Özellikler Penceresi](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Projenin bir kurumsal şablon projesinde nasıl dahil olduğunu ve bu kuruluş şablonu projesinin ilkeyi nasıl zorlayacağını açıklar.  
  
 [Özellikler Penceresi Alanları ve Arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 **Özellikler** penceresinde hangi bilgilerin görüntülendiğini belirleyen seçimin temelini açıklar.  
  
 [Özellikler Penceresi Nesne Listesi](../../extensibility/internals/properties-window-object-list.md)  
 Bu listedeki farklı bir nesnenin bir çağrıyı tetiklediği, ortamın yeni bir nesne seçilmiş olduğunu bilgilendirdiğini açıklayan **Özellikler** penceresi nesne listesinin amacını açıklar.  
  
 [Özellikler Penceresi Düğmeleri](../../extensibility/internals/properties-window-buttons.md)  
 **Özellikler** penceresi araç çubuğunda görünen dört varsayılan düğmenin amacını açıklar.  
  
 [Özellikler Görüntü Kılavuzu](../../extensibility/internals/properties-display-grid.md)  
 Özellik adlarının ve özellik değerleri alanlarının kılavuzda nerede bulunduğu açıklanmaktadır.  
  
 [Özellik penceresi seçim Izleme duyurusu](../../misc/announcing-property-window-selection-tracking.md)  
 **Özellikler** penceresi için seçim izlemeyi açıklar.  
  
 [Alt özellikleri olan özellikleri gizleme](../../misc/hiding-properties-that-have-child-properties.md)  
 Arabirimini uygulayarak alt özellikleri olan özelliklerin nasıl gizlendiği açıklanmaktadır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> .  
  
 [Özel Özellikler penceresi sağlama](../../misc/providing-a-custom-properties-window.md)  
 Kendi özellik tarayıcınızı sağlamaya yönelik adımların ayrıntılarına bakın.  
  
 [Özellikler penceresinden alan açıklamalarını alma](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Seçili özellik alanıyla ilgili bilgileri görüntüleyen Açıklama alanının nerede bulunacağını açıklar.  
  
 [Özellikler penceresinde özellik değerlerini güncelleştirme](../../misc/updating-property-values-in-the-properties-window.md)  
 **Özellikler** penceresini Özellik değeri değişiklikleriyle eşitlenmiş halde tutmanın iki yolunu gösteren adım adım yönergeler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Projeleri IDE 'nin yapı taşları olarak açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Derleme ve Oluşturma](../../ide/compiling-and-building-in-visual-studio.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Uygulamaları oluştururken sürekli test ve hata ayıklama için platformu nasıl kullanabileceğinizi açıklar.  
  
 [HTML belgesi özellikleri, Özellikler penceresi](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Bir HTML belgesini doğrudan Özellikler penceresi düzenlemeyle ilgili yönergeler sağlar ve Özellikler penceresi bir HTML belgesindeki alanları ayrıntılandıran bir tablo sağlar.  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 `IDispatch`Bir nesnenin yöntemleri ve özellikleri hakkında bilgi almak ve erişmek için bir geç bağlantılı mekanizma sağlamak üzere ilk olarak Otomasyonu destekleyecek şekilde tasarlanan arabirimi açıklar.  
  
 [NIB: dinamik özelliklere giriş (Visual Studio)](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Uygulamanızı, özellik değerlerinin uygulamanın derlenmiş kodu yerine bir dış yapılandırma dosyasında depolanması için yapılandırmanıza olanak sağlayan dinamik özelliklere genel bir bakış sağlar.  
  
 [NIB: kapsayıcılar olarak projeler](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Uygulamanızı oluşturan öğeleri mantıksal olarak yönetmek, derlemek ve hatalarını ayıklamak için bir çözümde kapsayıcı olarak projenin rolünü açıklar.  
  
 [NIB: proje özellikleri](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Projenin, projenin tamamına uygulanan özellikleri ve ayrıca projenin belirli derleme yapılandırmalarına sınırlı özellikleri denetlemenize olanak tanıyan ayarları nasıl yönettiğini açıklar.  
  
 [Çözümler ve projeler](../../ide/solutions-and-projects-in-visual-studio.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Çözümler ve projeler aracılığıyla geliştirme çabalarınız için gereken başvurular, veri bağlantıları, klasörler ve dosyalar gibi öğeleri verimli bir şekilde nasıl yönettiğini açıklar.  
  
 [Visual Studio’nun Diğer Bölümlerini Genişletme](../../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Hizmetlerin, geri kalanı ile eşleşen kullanıcı arabirimi öğeleri oluşturmak için nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
