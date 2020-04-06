---
title: Sihirbazlar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703205"
---
# <a name="wizards"></a>Sihirbazlar
Bir sihirbaz oluşturduktan sonra, genellikle diğerlerinin kullanabilmesi için tümleşik geliştirme ortamına [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) eklemek istersiniz. Eklenen sihirbaz daha sonra **Yeni Proje Ekle** veya **Yeni Öğe Ekle** iletişim kutularında görüntülenir. **Yeni Proje Ekle** veya Yeni Öğe **Ekle** iletişim kutularını görmek için **Çözüm Gezgini'nde**açık bir çözüme sağ tıklayın, **Ekle'ye**işaret edin ve ardından Yeni Proje veya **Yeni** **Öğe'yi**tıklatın.

 Sihirbazlar, kullanıcıların Yeni Proje Ekle iletişim kutusunu veya Yeni Öğe **Ekle** iletişim kutusunu açtıklarında **Add New Item** veya Solution Explorer'da bir öğeyi sağ tıklattıklarında kullanılabilir değerlerin ağaç görünümünden seçim yapabilsinler için uygulanabilir. **Solution Explorer** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

 Sihirbazınızda, yeni bir proje veya tekrarın adını yerelleştirme seçeneği sağlayabilir ve kullanıcıların sihirbazı seçtiklerinde görecekleri simgeyi belirleyebilirsiniz. Ayrıca, yeni öğelerin diğer kullanılabilir öğelere göre görünme sırasını da denetleyebilirsiniz; öğeleri alfabetik olarak düzenlenmesi gerekmez.

 Ayrıca, açıldığında sihirbaza geçirilen özel parametrelere bağlı olarak farklı başlayan bir sihirbaz da sağlayabilirsiniz.

 Bu bölümdeki konular, sihirbazınızı kullanılabilir sihirbazlar ve şablonlar arasında listelemek için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Yeni Proje Ekle** ve Yeni **Öğe Ekle** iletişim kutularına neden olmak için uyguladığınız dosyaları ve Sihirbazınızın IDE'de düzgün çalışması için karşılaması gereken gereksinimleri tartışır.

## <a name="in-this-section"></a>Bu Bölümde
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Hangi şablon dizin açıklaması dosyalarına genel bir bakış sağlar ve iletişim kutularında bir projeyle ilişkili klasörleri, sihirbaz .vsz dosyalarını ve şablon dosyalarını görüntülemek için IDE'de nasıl çalıştığını açıklar.

- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)

 IDE'nin sihirbazları nasıl başlattığını açıklar ve .vsz dosyasının üç bölümünü listeler.

- [Sihirbaz Arabirimi (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Sihirbazların `IDTWizard` IDE'de çalışması için uygulaması gereken arabirimi açıklar.

- [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md)

 Sihirbazların nasıl uygulandığını ve IDE Bağlam Parametrelerini uygulamaya geçtiğinde neler inanacağını açıklar.

- [Özel Parametreler](../../extensibility/internals/custom-parameters.md)

 Sihirbaz başladıktan sonra sihirbazın çalışmasını denetlemek için Özel Parametrelerin nasıl kullanılacağını açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Proje Türleri](../../extensibility/internals/project-types.md)

 Yeni proje türlerinin nasıl tasarlanış edilebildiğini anlatan ek konulara bağlantılar sağlar.

- [Projeleri Genişletme](../../extensibility/extending-projects.md)

 Kod dosyalarını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve kaynak dosyalarını düzenlemek için projelerin ve çözümlerin nasıl kullanılacağını ve kaynak denetiminin nasıl uygulanacağını açıklar.
