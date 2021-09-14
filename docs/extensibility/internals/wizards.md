---
title: Sihirbazlar | Microsoft Docs
description: sihirbazın, Visual Studio ' deki kullanılabilir sihirbazlar ve şablonlar arasında ve sihirbazın ıde 'de karşılaması gereken gereksinimler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8c652e67db103350a9e3fa92e08212422caae424
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726910"
---
# <a name="wizards"></a>Sihirbazlar
Sihirbaz oluşturduktan sonra, genellikle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başkalarının kullanabilmesi için tümleşik geliştirme ortamına (IDE) eklemek istersiniz. eklenen sihirbaz daha sonra **yeni Project ekle** veya **yeni öğe ekle** iletişim kutularında görünür. **yeni Project ekle** veya **yeni öğe ekle** iletişim kutularını görmek için, **Çözüm Gezgini** bir açık çözüme sağ tıklayın, **ekle**' nin üzerine gelin ve ardından **yeni Project** ya da **yeni öğe**' ye tıklayın.

 sihirbazlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , kullanıcıların **yeni Project ekle** iletişim kutusunu veya **yeni öğe ekle** iletişim kutusunu açtıklarında veya **Çözüm Gezgini** bir öğeye sağ tıkladıklarında kullanılabilir değerlerin ağaç görünümünden seçim yapmasına olanak sağlamak için ' de uygulanabilir.

 Sihirbazda, yeni bir proje ya da ITES adını yerelleştirme seçeneğini belirtebilir ve kullanıcıların Sihirbazı seçerken göreceği simgeyi belirleyebilirsiniz. Ayrıca, yeni öğelerin kullanılabilir diğer öğelere göre görünme sırasını da denetleyebilirsiniz; öğelerin alfabetik olarak organize olması gerekmez.

 Ayrıca, açıldığında sihirbaza geçirilen özel parametrelere dayalı olarak, farklı şekilde başlayan bir sihirbaz da sağlayabilirsiniz.

 bu bölümdeki konularda, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **yeni Project ekle** ve **yeni öğe ekle** iletişim kutularına, sihirbazın kullanılabilir sihirbazlar ve şablonlar arasında ve sihirbazın ıde 'de doğru şekilde çalışması için karşılaması gereken gereksinimler hakkında tartışın.

## <a name="in-this-section"></a>Bu Bölümde
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Şablon dizin açıklama dosyalarına genel bir bakış sağlar ve iletişim kutularındaki bir projeyle ilişkili klasörleri, sihirbaz. vsz dosyalarını ve şablon dosyalarını görüntüleme, IDE 'de nasıl çalıştığını açıklar.

- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)

 IDE 'nin sihirbazları nasıl başlattığı ve. vsz dosyasının üç parçasını listeleyen açıklanır.

- [Sihirbaz Arabirimi (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 `IDTWizard`SIHIRBAZLARıN IDE 'de çalışmak için uygulaması gereken arabirimi açıklar.

- [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)

 Sihirbazların nasıl uygulandığını ve IDE 'nin uygulamaya bağlam parametrelerini geçirdiğinde ne olduğunu açıklar.

- [Özel parametreler](../../extensibility/internals/custom-parameters.md)

 Sihirbaz başlatıldıktan sonra sihirbazın işlemini denetlemek için özel parametrelerin nasıl kullanılacağını açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Proje Türleri](../../extensibility/internals/project-types.md)

 Yeni proje türlerinin nasıl tasarlanabileceği hakkında bilgi sunan ek konuların bağlantılarını sağlar.

- [Projeleri Genişletme](../../extensibility/extending-projects.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kod dosyalarını ve kaynak dosyalarını düzenlemek için projelerin ve çözümlerin nasıl kullanılacağını ve kaynak denetiminin nasıl uygulanacağını açıklar.
