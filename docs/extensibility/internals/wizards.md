---
title: Sihirbazlar | Microsoft Docs
description: Sihirbazlarınızı, sihirbazda kullanılabilir sihirbazlar ve şablonlar arasında nasıl listeleyebilirsiniz Visual Studio sihirbazının IDE'de karşılaması gereken gereksinimler hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: 3dfd9aa95b44fff288f13cf106366da94f73f845d9bb2ad4626830d8b6fe7b02
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375432"
---
# <a name="wizards"></a>Sihirbazlar
Bir sihirbaz oluşturduk sonra, bunu genellikle başkalarının kullanamı için tümleşik geliştirme ortamına [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) eklemek istersiniz. Eklenen sihirbaz daha sonra Yeni Öğe **Ekle veya Project** ekle iletişim **kutularında** görünür. Yeni Uygulama Ekle veya **Project**  Öğe Ekle iletişim kutularını görmek için, **Çözüm Gezgini'de** bir açık çözüme sağ tıklayın, Ekle'nin üzerine gelin ve ardından Yeni Project **veya** **Yeni Öğe'ye tıklayın.**

 Sihirbazlar, kullanıcıların Yeni Project Ekle iletişim kutusunu veya Yeni Öğe Ekle iletişim kutusunu açtıklarında veya Çözüm Gezgini'da bir öğeye sağ tıklarken kullanılabilir değerlerin ağaç görünümünden seçimlerini yapmak için 'de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Çözüm Gezgini.**  

 Sihirbazda, yeni bir projenin veya projenin adını yerelleştirme seçeneğini sebilirsiniz ve sihirbazı seçen kullanıcıların göreceği simgeyi belirleyebilirsiniz. Ayrıca, yeni öğelerin diğer kullanılabilir öğelere göre görünme sıralamalarını da kontrol etmek için; öğelerin alfabetik olarak düzenlenmiş olması gerek değildir.

 Ayrıca, sihirbaz açıldığında sihirbaza geçirilen özel parametrelere bağlı olarak farklı şekilde başlayan bir sihirbaz da sebilirsiniz.

 Bu bölümdeki konular, kullanılabilir sihirbazlar ve şablonlar arasında sihirbazınızı listeleye yeni Project ve Yeni Öğe Ekle iletişim kutularının neden olduğu dosyaları ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  sihirbazın IDE'de doğru şekilde çalışması için karşılaması gereken gereksinimleri tartışmaktadır. 

## <a name="in-this-section"></a>Bu Bölümde
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Hangi şablon dizini açıklama dosyalarına genel bir bakış sağlar ve iletişim kutularında bir projeyle ilişkili klasörleri, sihirbaz .vsz dosyalarını ve şablon dosyalarını görüntülemek için IDE'de nasıl olduklarını açıklar.

- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)

 IDE'nin sihirbazları nasıl başlatıyor ve .vsz dosyasının üç bölümlerini listeler.

- [Sihirbaz Arabirimi (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Sihirbazların `IDTWizard` IDE'de çalışmak için uygulaması gereken arabirimi açıklar.

- [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md)

 Sihirbazların nasıl uygulandığını ve IDE'nin uygulamaya Bağlam Parametrelerini geçirip ne olduğunu açıklar.

- [Özel Parametreler](../../extensibility/internals/custom-parameters.md)

 Sihirbaz başlatıldıktan sonra sihirbazın işlemlerini kontrol etmek için Özel Parametrelerin nasıl kullanılası açıklanıyor.

## <a name="related-sections"></a>İlgili Bölümler
- [Proje Türleri](../../extensibility/internals/project-types.md)

 Yeni proje türleri tasarlama hakkında bilgi sunan ek konu başlıklarına bağlantılar sağlar.

- [Projeleri Genişletme](../../extensibility/extending-projects.md)

 Kod dosyalarını ve kaynak dosyalarını düzenlemek için projelerin ve çözümlerin nasıl kullanıldığını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve kaynak denetimin nasıl uygulandığını açıklar.
