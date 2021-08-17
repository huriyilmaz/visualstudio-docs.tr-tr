---
title: Öğe Project Project Ekleme | Microsoft Docs
description: Tümleşik geliştirme ortamında (IDE) proje ve proje öğesi şablonlarını Visual Studio iletişim kutularına eklemeyi öğrenin.
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
ms.openlocfilehash: ae29f7d2d2e15cacc56d7c3fb42e7b86ee31be903032dc55dd5a61276360449d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376436"
---
# <a name="add-project-and-project-item-templates"></a>Proje ve proje öğesi şablonları ekleme
Kendi proje türlerinizi oluşturma aşamasında, standart tümleşik geliştirme ortamı (IDE) iletişim kutularını kullanarak yeni projeler ve proje öğeleri ekleme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desteği sağlamalıdır. Aşağıdaki konular, proje ve proje öğeleri eklemeye yönelik farklı teknikleri ele amaktadır.

## <a name="in-this-section"></a>Bu bölümde
- [Project bağlamı](../../extensibility/internals/project-context.md)

 Projenin ortamdaki geçici durumlara ilişkin bağlam bilgisinin çoğunu sağladığını açıklar.

- [Project önceliği](../../extensibility/internals/project-priority.md)

 Bir proje öğesinin, öğeyi açmak için kullanılan projeyle ilgili belirsizlikten kaçınmaya yardımcı olmak için genellikle bir projenin üyesi olduğunu açıklar.

- [Çeşitli Dosyalar projesi](../../extensibility/internals/miscellaneous-files-project.md)

 Bir projede dosyaları açmak için kullanılan iki düzenleyici türü ve proje öğesi açıldığında kullanılacak düzenleyiciyi belirlemede projenin oynadığı rol hakkında bilgi sağlar.

- [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)

 Bir proje oluşturulduğunda ne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olduğunu açıklar.

- [Yeni Öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Yeni Öğe Ekle iletişim kutusuna öğe **ekleme işlemini** açıklar.

- [Yeni Dizinler iletişim kutusuna Project ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 VSPackage tarafından kullanılabilir olan özel şablonlar içeren yeni bir dizin kaydetme örneği sağlar.

- [Yeni Öğe Ekle iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Yeni Öğe Ekle iletişim kutusu için yeni bir dizin kümesi **kaydetme örneği** sağlar.

- [Proje sistemlerini genişletmek için IDE tanımlı komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Proje sistemlerini genişletmek için kullanılan farklı türlerde komut öğelerini listeler.

- [Projeleri genişletmek için genellikle kullanılan nesneler için CATID'ler](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 , ve proje sistemlerini genişletmek için kullanılan nesnelerin [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] CATID'lerini [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] listeler.

## <a name="related-sections"></a>İlgili bölümler
- [Nasıllı: Projeye özgü düzenleyicileri açma](../../extensibility/how-to-open-project-specific-editors.md)

 Bir proje için belirli bir düzenleyiciye içsel olarak bağlı bir öğeyi açmak için adım adım yönergeler sağlar.

- [Nasıl: Standart düzenleyicileri açma](../../extensibility/how-to-open-standard-editors.md)

 Standart düzenleyiciyi açmak için adım adım yönergeler sağlar.

- [Project alt türleri](../../extensibility/internals/project-subtypes.md)

 Proje alt türü kavramsal konularına bağlantılar sağlar. Project ve projelerini genişleten [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] alt [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] türler vardır.

- [Project türleri](../../extensibility/internals/project-types.md)

 Yeni proje türleri tasarlama hakkında bilgi sunan ek konu başlıklarına bağlantılar sağlar.
