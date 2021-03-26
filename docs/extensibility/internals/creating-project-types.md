---
title: Proje türleri oluşturuluyor | Microsoft Docs
description: Programlama görevlerini destekleyen yeni bir proje türü tasarlayarak, oluşturarak ve kaydederek Visual Studio 'Yu genişletmeyi öğrenin.
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
ms.workload:
- vssdk
ms.openlocfilehash: 5984afd2879f94a73ef02f77a85501c50f55bc93
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056824"
---
# <a name="create-project-types"></a>Proje türleri oluştur
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Yeni bir proje türü oluşturarak genişletebilirsiniz. Yeni bir proje türü oluşturmak için birkaç kavram anlamalı ve bir dizi adımı tamamlamalısınız. Aşağıdaki konular, proje türlerinin nasıl oluşturulacağı hakkında genel bakış sağlar.

## <a name="in-this-section"></a>Bu bölümde
- [Proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md)

 Yeni bir proje türü oluşturmadan önce yapmanız gereken öğe, proje dosyası kalıcılığı ve taahhüt mekanizması tasarım kararlarını açıklar.

- [Denetim listesi: yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)

 Kod Düzenle ve projenizde uygulama derleme, derleme, hata ayıklama ve dağıtma gibi programlama görevlerini destekleyen yeni bir proje türü oluşturmak için izlemeniz gereken adımlara genel bir bakış sağlar.

- [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Yeni bir projenin örneklerini oluşturmak için bir proje fabrikası sağlama ve kullanma hakkında bilgi sağlar.

- [Proje türünü kaydetme](../../extensibility/internals/registering-a-project-type.md)

 Kayıt defterinden varsayılan yolları ve verileri sağlayan deyimlerin kod örneklerini ve her bir deyimin kayıt defteri betiğinin girdilerini içeren bir tabloyu sağlar.

- [Proje kalıcılığı](../../extensibility/internals/project-persistence.md)

 `IPersistFileFormat`Hem dosya hem de dosya tabanlı olmayan proje nesnelerini kalıcı hale getirmek için kullanımını açıklar.

- [MSBuild kullanma](../../extensibility/internals/using-msbuild.md)

 Proje tipinin, [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] kullanıcıların [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , komut satırından ve ' den derlenmesi için yapı altyapısını nasıl kullanabilecebileceğinizi açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Destek sembolü-tarama araçları](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 **Nesne tarayıcısı** ve **sınıf görünümü** penceresi gibi kod görüntüleme araçlarının mimarisini açıklar. VSPackage 'ta nesne taramayı uygulamak için kullanılan arabirimleri ve yöntemleri açıklar.

- [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Proje öğesi açıldığında ve proje kaynaklarının nasıl işlenebileceği hakkında hangi düzenleyicinin kullanıldığını belirlemek için projelerin oynadığı önemi açıklar.

- [Windows Installer ile VSPackages 'i yükler](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 VSPackage 'un kendi benzersiz kimliği ve bir Windows Installer paketindeki VSPackage dll 'larınızı ve diğer bilgileri nasıl sarılacağını gösterir (*. MSI* dosyası) müşterilere dağıtım için.

- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Görünümlerin ve adreslerin hiyerarşilerini açıklar.

- [VSPackage’lar](../../extensibility/internals/vspackages.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Ortamı genişleten ve kendi VSPackage 'ı nasıl uygulayacağınızı ele alan, yüklenebilen BIR com nesnesi olan VSPackage 'a genel bir bakış sağlar.

- [Proje türleri](../../extensibility/internals/project-types.md)

 Kodu değiştirmek, kod derlemek ve derlemek ve kodu çalıştırmak ve hata ayıklamak için projelerin nasıl kullanılacağını açıklar ve proje türlerinin nasıl oluşturulacağı hakkında ayrıntılı konulara bağlantılar sağlar.
