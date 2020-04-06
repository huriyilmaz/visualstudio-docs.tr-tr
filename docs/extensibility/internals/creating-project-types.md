---
title: Proje Türleri Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709077"
---
# <a name="create-project-types"></a>Proje türleri oluşturma
Yeni bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje türü oluşturarak genişletebilirsiniz. Yeni bir proje türü oluşturmak için, birkaç kavramı anlamanız ve birkaç adımı tamamlamanız gerekir. Aşağıdaki konular, proje türlerinin nasıl oluşturulaca ilgili genel bir bakış sağlar.

## <a name="in-this-section"></a>Bu bölümde
- [Proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md)

 Yeni bir proje türü oluşturmadan önce oluşturmanız gereken öğeyi, proje dosyası kalıcılığını ve taahhüt mekanik tasarım kararlarını tartışır.

- [Denetim Listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)

 Kod düzenleme ve düzenleme, oluşturma, hata ayıklama ve projenizde uygulamaları dağıtma gibi programlama görevlerini destekleyen yeni bir proje türü oluşturmak için izlemeniz gereken adımlara genel bir bakış sağlar.

- [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Yeni bir proje örnekleri oluşturmak için proje fabrikasının nasıl sağlanıp kullanılacağı hakkında bilgi sağlar.

- [Proje türünü kaydetme](../../extensibility/internals/registering-a-project-type.md)

 Varsayılan yollar ve veriler sağlayan kayıt defterinden gelen ifadelerin kod örneklerini ve her deyim için kayıt defteri komut dosyasından girişleri içeren bir tablo sağlar.

- [Proje kalıcılığı](../../extensibility/internals/project-persistence.md)

 Hem dosya hem `IPersistFileFormat` de dosya tabanlı olmayan proje nesnelerini kalıcı olarak sürdürmek için kullanımını tartışır.

- [MSBuild kullanma](../../extensibility/internals/using-msbuild.md)

 Proje türünün, kullanıcıların [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] komut satırından ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut satırında oluşturmalarına izin vermek için yapı altyapısını nasıl kullanabileceğini açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Sembol tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 **Nesne Tarayıcısı** ve **Sınıf Görünümü** penceresi gibi kod görüntüleme araçlarının mimarisini açıklar. VSPackage'da nesne taramasını uygulamak için kullanılan arabirimleri ve yöntemleri açıklar.

- [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Bir proje öğesi açıldığında hangi düzenleyicinin kullanıldığını ve proje kaynaklarının nasıl manipüle edilebildiğini belirlemede projelerin oynadığı önemi tartışır.

- [Windows Installer ile VSPackages yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 VSPackage'ınıza kendi benzersiz kimliğini nasıl vereceğinizve VSPackage DL'lerinizi ve diğer bilgilerinizi bir Windows Yükleyici paketine nasıl sarın gösterir (*. MSI* dosyası) müşterilerinize dağıtım için.

- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Görünümleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve adresleri hiyerarşileri açıklar.

- [VSPackage’lar](../../extensibility/internals/vspackages.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Çevreyi genişleten ve kendi VSPackage'ınızı nasıl uygulayacağınızı anlatan yüklenebilir bir COM nesnesi olan VSPackage'a genel bir bakış sağlar.

- [Proje türleri](../../extensibility/internals/project-types.md)

 Kodu değiştirmek, kodu derlemek ve oluşturmak için projelerin nasıl kullanılacağını tartışır, kodu çalıştırır ve hata ayıklama sağlar ve proje türlerinin nasıl oluşturulaca ilişkin ayrıntılı konulara bağlantılar sağlar.
