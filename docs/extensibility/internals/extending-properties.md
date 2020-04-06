---
title: Genişletme Özellikleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708426"
---
# <a name="extend-properties"></a>Özellikleri genişletme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Özellikler** penceresi COM ve COM+ bileşenleri için evrensel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir özellik tarayıcısıdır ve tüm ürünleri destekler. **Özellikler** penceresi, `ITypeInfo` tümleşik geliştirme ortamındaki (IDE) herhangi bir pencerede şu anda seçili nesnenin tasarım zamanı özelliklerini listelemek için tür bilgileri ve COM+ meta verileriyle birlikte çalışır.

 Klavyede **F4** tuşuna basarak veya **Görünüm** menüsünde **Özellikler Penceresi** seçilerek açılabilir **Özellikleri** penceresi, yapılandırmadan bağımsız, tasarım süresi özellikleri ve seçili nesnelerin olaylarını görüntülemek ve düzenlemek için kullanılır. Çözümler ve projelerle ilişkili yapılandırmaya bağımlı özellikler [Özellik sayfalarında](../../extensibility/internals/property-pages.md)görüntülenir. Daha fazla bilgi için [yapılandırma seçeneklerini yönetin.](../../extensibility/internals/managing-configuration-options.md)

 ![Özellikler penceresine genel bakış](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Özellikler penceresi

 Bu bölümde, **Özellikler** penceresinin tek tek alanları ve pencereyi doldurmak için uygulamanız ve aramanız gereken arabirimlerle ilgili ayrıntılı bilgiler bulunur.

## <a name="in-this-section"></a>Bu bölümde
- [Özellikler penceresine genel bakış](../../extensibility/internals/properties-window-overview.md)

 Araç penceresi ve belge penceresine göre **Özellikler** penceresinin amacını açıklar.

- [Şablon ilkesi ve Özellikler penceresi](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Bir projenin kurumsal şablon projesinde nasıl yer almasını ve bu kuruluş şablonu projesinin ilkeyi nasıl uygulayabileceğini tartışır.

- [Pencere alanlarını ve arabirimlerini özellikleri](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 **Özellikler** penceresinde hangi bilgilerin görüntüleneceğini belirleyen seçimin temelini açıklar.

- [Özellikler penceresi nesne listesi](../../extensibility/internals/properties-window-object-list.md)

 **Özellikler** penceresi nesne listesinin amacını açıklar ve bu listeden farklı bir nesne aramayı tetiklediğinde ortamın nasıl yeni bir nesne seçildiğini açıklar.

- [Özellikler pencere düğmeleri](../../extensibility/internals/properties-window-buttons.md)

 **Özellikler** penceresi araç çubuğunda görüntülenen dört varsayılan düğmenin amacını açıklar.

- [Özellikler görüntü ızgarası](../../extensibility/internals/properties-display-grid.md)

 Kılavuzda özellik adları ve özellik değerleri alanlarının nerede bulunduğunu açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Proje türleri](../../extensibility/internals/project-types.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projeleri IDE'nin yapı taşları olarak ele almaktadır.

- [Derleme ve oluşturma](../../ide/compiling-and-building-in-visual-studio.md)

 Platform,uygulamaları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluştururken sürekli olarak test etmek ve hata ayıklama için platformu nasıl kullanabileceğinizi açıklar.

- [ıdispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 İlk `IDispatch` olarak otomasyonu desteklemek üzere tasarlanan arabirimi açıklar ve bir nesnenin yöntemleri ve özellikleri hakkında bilgilere erişmek ve bilgi almak için geç bağlantı mekanizması sağlar.

- [Uygulama ayarlarını yönetme (.NET)](../../ide/managing-application-settings-dotnet.md)

 Özellik değerlerinin uygulamanın derlenmiş kodu yerine harici bir yapılandırma dosyasında depolanabilmesi için uygulamanızı yapılandırmanıza izin veren uygulama ayarlarına genel bir bakış sağlar.

- [Çözümler ve projeler](../../ide/solutions-and-projects-in-visual-studio.md)

 Çözümler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve projeler aracılığıyla geliştirme çabanız tarafından gerekli olan başvurular, veri bağlantıları, klasörler ve dosyalar gibi öğeleri ne kadar verimli bir şekilde yönettiğini açıklar.

- [Visual Studio'nun diğer bölümlerini genişletin](../../extensibility/extending-other-parts-of-visual-studio.md)

 Geri kalanıyla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eşleşen UI öğeleri oluşturmak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hizmetlerin nasıl kullanılacağını açıklar.
