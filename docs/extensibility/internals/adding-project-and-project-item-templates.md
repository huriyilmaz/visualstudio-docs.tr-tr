---
title: Proje ve proje öğesi şablonları ekleme | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamındaki (IDE) iletişim kutularına proje ve proje öğesi şablonları ekleme hakkında bilgi edinin.
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
ms.workload:
- vssdk
ms.openlocfilehash: 3f2c10b310569a412025fd114f7818734106bc18
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079065"
---
# <a name="add-project-and-project-item-templates"></a>Proje ve proje öğesi şablonları ekleme
Kendi proje türlerinizi oluştururken, standart [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE) iletişim kutularını kullanarak yeni projeler ve proje öğeleri ekleme desteği sağlamanız gerekir. Aşağıdaki konularda projeler ve proje öğeleri eklemek için farklı teknikler ele alınmaktadır.

## <a name="in-this-section"></a>Bu bölümde
- [Proje bağlamı](../../extensibility/internals/project-context.md)

 Projenin, ortamda transpires için bağlam bilgilerinin çoğunu sağladığını açıklar.

- [Proje önceliği](../../extensibility/internals/project-priority.md)

 Öğe açmak için hangi projenin kullanıldığı hakkında belirsizliğe engel olmak için bir proje öğesinin genellikle bir projenin üyesi olduğunu açıklar.

- [Çeşitli dosyalar projesi](../../extensibility/internals/miscellaneous-files-project.md)

 Bir projede dosyaları açmak için kullanılabilecek iki Düzenleyici türü ve proje öğesi açıldığında hangi düzenleyicinin kullanılacağını belirlemek için projenin oynadığı rol hakkında bilgi sağlar.

- [Proje ve öğe şablonlarını Kaydet](../../extensibility/internals/registering-project-and-item-templates.md)

 Proje oluşturulduğunda ne olduğunu açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Yeni öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 **Yeni öğe Ekle** iletişim kutusuna öğe ekleme işlemini açıklar.

- [Yeni proje iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

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

- [Proje alt türleri](../../extensibility/internals/project-subtypes.md)

 Project Subtype kavramsal konularına bağlantılar sağlar. Proje alt türleri mevcut [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projeleri genişletmelidir.

- [Proje türleri](../../extensibility/internals/project-types.md)

 Yeni proje türlerinin nasıl tasarlanabileceği hakkında bilgi sunan ek konuların bağlantılarını sağlar.
