---
title: Proje ve Proje Öğesi Şablonları Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710201"
---
# <a name="add-project-and-project-item-templates"></a>Proje ve proje öğesi şablonları ekleme
Kendi proje türlerinizi oluşturduğunuzda, standart [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE) iletişim kutularını kullanarak yeni projeler ve proje öğeleri eklemek için destek sağlamanız gerekir. Aşağıdaki konular, proje ve proje öğeleri eklemek için farklı teknikler tartışır.

## <a name="in-this-section"></a>Bu bölümde
- [Proje bağlamı](../../extensibility/internals/project-context.md)

 Projenin, çevrede neler indiğinin bağlam bilgilerinin çoğunu sağladığını açıklar.

- [Proje önceliği](../../extensibility/internals/project-priority.md)

 Bir proje öğesinin, öğeyi açmak için hangi projenin kullanıldığı yla ilgili belirsizliği önlemeye yardımcı olmak için genellikle bir projenin üyesi olduğunu açıklar.

- [Çeşitli Dosyalar projesi](../../extensibility/internals/miscellaneous-files-project.md)

 Projedeki dosyaları açmak için kullanılabilecek iki düzenleyici türü ve proje öğesi açıldığında hangi düzenleyicinin kullanılacağını belirlemede projenin oynadığı rol hakkında bilgi sağlar.

- [Proje ve madde şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)

 Proje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturulduğunda ne olduğunu açıklar.

- [Yeni Öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 **Yeni Öğe Ekle** iletişim kutusuna öğe ekleme işlemini açıklar.

- [Yeni Proje iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 VSPackage tarafından sunulan özel şablonlar içeren yeni bir dizin kaydetme örneği sağlar.

- [Yeni Öğe Ekle iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 **Yeni Öğe Ekle** iletişim kutusu için yeni bir dizin kümesi kaydetme örneği sağlar.

- [Proje sistemlerini genişletmek için IDE tanımlı komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Proje sistemlerini genişletmek için kullanılan farklı komut öğeleri türlerini listeler.

- [Genellikle projeleri genişletmek için kullanılan nesnelerin CATID'leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Genişletme ve [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proje sistemlerini genişletmek için kullanılan nesneler için CATID'leri listeler.

## <a name="related-sections"></a>İlgili bölümler
- [Nasıl açılır: Projeye özel düzenleyicileri açın](../../extensibility/how-to-open-project-specific-editors.md)

 Bir proje için belirli bir düzenleyiciye bağlı bir öğeyi açmak için adım adım yönergeler sağlar.

- [Nasıl yapılsın: Standart düzenleyicileri açın](../../extensibility/how-to-open-standard-editors.md)

 Standart bir düzenleyici açmak için adım adım yönergeler sağlar.

- [Proje alt türleri](../../extensibility/internals/project-subtypes.md)

 Proje alt türü kavramsal konulara bağlantılar sağlar. Proje alt türleri [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] varolan ve projeleri genişletir.

- [Proje türleri](../../extensibility/internals/project-types.md)

 Yeni proje türlerinin nasıl tasarlanış edilebildiğini anlatan ek konulara bağlantılar sağlar.
