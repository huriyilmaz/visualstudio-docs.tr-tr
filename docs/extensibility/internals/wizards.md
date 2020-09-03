---
title: Sihirbazlar | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703205"
---
# <a name="wizards"></a>Sihirbazlar
Sihirbaz oluşturduktan sonra, genellikle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başkalarının kullanabilmesi için tümleşik geliştirme ortamına (IDE) eklemek istersiniz. Eklenen sihirbaz daha sonra **Yeni Proje Ekle** veya **Yeni öğe Ekle** iletişim kutularında görünür. **Yeni Proje Ekle** veya **Yeni öğe Ekle** iletişim kutularını görmek için **Çözüm Gezgini**bir açık çözüme sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni proje** veya **Yeni öğe**' ye tıklayın.

 Sihirbazlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , kullanıcıların **Yeni Proje Ekle** Iletişim kutusunu veya **Yeni öğe Ekle** iletişim kutusunu açtıklarında veya **Çözüm Gezgini**bir öğeye sağ tıkladıklarında kullanılabilir değerlerin ağaç görünümünden seçim yapmasına olanak sağlamak için ' de uygulanabilir.

 Sihirbazda, yeni bir proje ya da ITES adını yerelleştirme seçeneğini belirtebilir ve kullanıcıların Sihirbazı seçerken göreceği simgeyi belirleyebilirsiniz. Ayrıca, yeni öğelerin kullanılabilir diğer öğelere göre görünme sırasını da denetleyebilirsiniz; öğelerin alfabetik olarak organize olması gerekmez.

 Ayrıca, açıldığında sihirbaza geçirilen özel parametrelere dayalı olarak, farklı şekilde başlayan bir sihirbaz da sağlayabilirsiniz.

 Bu bölümdeki konularda, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Yeni Proje Ekle** ve **Yeni öğe Ekle** iletişim kutularının, sihirbazın kullanılabilir sihirbazlar ve şablonlar arasında ve sihirbazın IDE 'de doğru şekilde çalışması için karşılaması gereken gereksinimler hakkında tartışın.

## <a name="in-this-section"></a>Bu Bölümde
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Şablon dizin açıklama dosyalarına genel bir bakış sağlar ve iletişim kutularındaki bir projeyle ilişkili klasörleri, sihirbaz. vsz dosyalarını ve şablon dosyalarını görüntüleme, IDE 'de nasıl çalıştığını açıklar.

- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)

 IDE 'nin sihirbazları nasıl başlattığı ve. vsz dosyasının üç parçasını listeleyen açıklanır.

- [Sihirbaz Arabirimi (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 `IDTWizard`SIHIRBAZLARıN IDE 'de çalışmak için uygulaması gereken arabirimi açıklar.

- [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md)

 Sihirbazların nasıl uygulandığını ve IDE 'nin uygulamaya bağlam parametrelerini geçirdiğinde ne olduğunu açıklar.

- [Özel Parametreler](../../extensibility/internals/custom-parameters.md)

 Sihirbaz başlatıldıktan sonra sihirbazın işlemini denetlemek için özel parametrelerin nasıl kullanılacağını açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Proje Türleri](../../extensibility/internals/project-types.md)

 Yeni proje türlerinin nasıl tasarlanabileceği hakkında bilgi sunan ek konuların bağlantılarını sağlar.

- [Projeleri Genişletme](../../extensibility/extending-projects.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kod dosyalarını ve kaynak dosyalarını düzenlemek için projelerin ve çözümlerin nasıl kullanılacağını ve kaynak denetiminin nasıl uygulanacağını açıklar.
