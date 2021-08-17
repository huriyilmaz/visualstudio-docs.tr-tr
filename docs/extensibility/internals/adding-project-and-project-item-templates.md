---
title: Project ve Project öğesi şablonları ekleme | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamındaki (ıde) iletişim kutularına proje ve proje öğesi şablonları ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 703c8db7dcc8245719ca9c8abba98653254260ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029144"
---
# <a name="add-project-and-project-item-templates"></a>Proje ve proje öğesi şablonları ekleme
Kendi proje türlerinizi oluştururken, standart [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE) iletişim kutularını kullanarak yeni projeler ve proje öğeleri ekleme desteği sağlamanız gerekir. Aşağıdaki konularda projeler ve proje öğeleri eklemek için farklı teknikler ele alınmaktadır.

## <a name="in-this-section"></a>Bu bölümde
- [Project bağlamı](../../extensibility/internals/project-context.md)

 Projenin, ortamda transpires için bağlam bilgilerinin çoğunu sağladığını açıklar.

- [Project önceliği](../../extensibility/internals/project-priority.md)

 Öğe açmak için hangi projenin kullanıldığı hakkında belirsizliğe engel olmak için bir proje öğesinin genellikle bir projenin üyesi olduğunu açıklar.

- [Çeşitli dosyalar projesi](../../extensibility/internals/miscellaneous-files-project.md)

 Bir projede dosyaları açmak için kullanılabilecek iki Düzenleyici türü ve proje öğesi açıldığında hangi düzenleyicinin kullanılacağını belirlemek için projenin oynadığı rol hakkında bilgi sağlar.

- [Proje ve öğe şablonlarını Kaydet](../../extensibility/internals/registering-project-and-item-templates.md)

 Proje oluşturulduğunda ne olduğunu açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Yeni öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 **Yeni öğe Ekle** iletişim kutusuna öğe ekleme işlemini açıklar.

- [yeni Project iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 VSPackage tarafından kullanılabilir hale getirilen özel şablonları içeren yeni bir dizin kaydetme örneği sağlar.

- [Yeni öğe Ekle iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 **Yeni öğe Ekle** iletişim kutusu için yeni bir dizin kümesi kaydetmenin bir örneğini sağlar.

- [Proje sistemlerini genişletmek için IDE tanımlı komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Proje sistemlerini genişletmek için kullanılan farklı komut öğesi türlerini listeler.

- [Projeleri genişletmek için genellikle kullanılan nesneler için CATIDs](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Ve proje sistemlerini genişletmek için kullanılan nesneler Için CATIDs 'leri listeler [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .

## <a name="related-sections"></a>İlgili bölümler
- [Nasıl yapılır: projeye özgü düzenleyiciler açma](../../extensibility/how-to-open-project-specific-editors.md)

 Bir proje için belirli bir düzenleyiciye bağlanacak bir öğe doğası gereği açmak için adım adım yönergeler sağlar.

- [Nasıl yapılır: standart düzenleyiciler açma](../../extensibility/how-to-open-standard-editors.md)

 Standart bir düzenleyiciyi açmak için adım adım yönergeler sağlar.

- [Project alt türleri](../../extensibility/internals/project-subtypes.md)

 Project Subtype kavramsal konularına bağlantılar sağlar. Project alt türleri var olan [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve projeleri genişletmelidir [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .

- [Project türleri](../../extensibility/internals/project-types.md)

 Yeni proje türlerinin nasıl tasarlanabileceği hakkında bilgi sunan ek konuların bağlantılarını sağlar.
