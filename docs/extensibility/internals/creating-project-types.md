---
title: Project Türleri | Microsoft Docs
description: Programlama görevlerini destekleyen Visual Studio proje türü tasarlar, oluşturarak ve kaydederek bu tür projelerin nasıl genişletici olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d4793bd69ffba676081139d61c0d81bcef4c336c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086670"
---
# <a name="create-project-types"></a>Proje türleri oluşturma
Yeni bir proje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] türü oluşturarak genişletin. Yeni bir proje türü oluşturmak için çeşitli kavramları anlamanız ve birkaç adımı tamamlamanız gerekir. Aşağıdaki konular, proje türlerinin nasıl oluşturularak ilgili genel bir bakış sağlar.

## <a name="in-this-section"></a>Bu bölümde
- [Project türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md)

 Yeni bir proje türü oluşturmadan önce vermeniz gereken öğeyi, proje dosyasının kalıcılığını ve taahhüt tasarım kararlarını tartışır.

- [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)

 Kodu düzenleme ve derleme, derleme, hata ayıklama ve projenize uygulama dağıtma gibi programlama görevlerini destekleyen yeni bir proje türü oluşturmak için izlemeniz gereken adımlara genel bir bakış sağlar.

- [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Yeni bir projenin örneklerini oluşturmak için proje fabrikası sağlama ve kullanma hakkında bilgi sağlar.

- [Proje türünü kaydetme](../../extensibility/internals/registering-a-project-type.md)

 Varsayılan yolları ve verileri sağlayan kayıt defterindeki deyimlerin kod örneklerini ve her deyimi için kayıt defteri betiğinden girdileri içeren bir tablo sağlar.

- [Project kalıcılık](../../extensibility/internals/project-persistence.md)

 Hem dosya hem de `IPersistFileFormat` dosya tabanlı olmayan proje nesnelerini kalıcı yapmak için kullanımını tartışır.

- [MSBuild kullanma](../../extensibility/internals/using-msbuild.md)

 Proje türlerinizi, kullanıcıların komut satırına ve komut satırına göre derlemesine izin [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] verme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] altyapısını nasıl kullanabileceğini açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Sembol tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Object Browser ve Sınıf Görünümü penceresi **gibi kod** **görüntüleme araçlarının mimarisini** açıklar. VSPackage'da nesne tarama uygulamak için kullanılan arabirimleri ve yöntemleri açıklar.

- [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Projelerin, bir proje öğesi açıldığında hangi düzenleyicinin kullanılı olduğunu ve proje kaynaklarının nasıl değiştirilip değiştirilene karar verir.

- [WINDOWS Yükleyicisi ile VSPackage'ları yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 VSPackage'nıza kendi benzersiz kimliğini verme ve VSPackage DLL'lerinizi ve diğer bilgileri müşterilerinize dağıtım için Windows Yükleyici paketinde *(.MSI* dosyası) sarmalayı gösterir.

- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Görünümlerin ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adreslerin hiyerarşileri nasıl işley olduğunu açıklar.

- [VSPackage’lar](../../extensibility/internals/vspackages.md)

 Ortamı genişleten ve kendi VSPackage'nızı nasıl uygulayacaklarını tartışan, yüklenebilir bir COM nesnesi olan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'a genel bir bakış sağlar.

- [Project türleri](../../extensibility/internals/project-types.md)

 Kodu değiştirmek, derlemek ve kod derlemek, kodu çalıştırmak ve hata ayıklamak için projelerin nasıl kullanılır ve proje türleri oluşturma hakkında ayrıntılı konulara bağlantılar sağlar.
