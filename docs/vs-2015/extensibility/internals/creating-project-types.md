---
title: Proje türleri oluşturuluyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155036"
---
# <a name="creating-project-types"></a>Proje Türleri Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Yeni bir proje türü oluşturarak genişletebilirsiniz. Yeni bir proje türü oluşturmak için birkaç kavram anlamalı ve bir dizi adımı tamamlamalısınız. Aşağıdaki konular, proje türlerinin nasıl oluşturulacağı hakkında genel bakış sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Proje Türü Tasarım Kararları](../../extensibility/internals/project-type-design-decisions.md)  
 Yeni bir proje türü oluşturmadan önce yapmanız gereken öğe, proje dosyası kalıcılığı ve taahhüt mekanizması tasarım kararlarını açıklar.  
  
 [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Kod Düzenle ve projenizde uygulama derleme, derleme, hata ayıklama ve dağıtma gibi programlama görevlerini destekleyen yeni bir proje türü oluşturmak için izlemeniz gereken adımlara genel bir bakış sağlar.  
  
 [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Yeni bir projenin örneklerini oluşturmak için bir proje fabrikası sağlama ve kullanma hakkında bilgi sağlar.  
  
 [Proje Türü Kaydetme](../../extensibility/internals/registering-a-project-type.md)  
 Kayıt defterinden varsayılan yolları ve verileri sağlayan deyimlerin kod örneklerini ve her bir deyimin kayıt defteri betiğinin girdilerini içeren bir tabloyu sağlar.  
  
 [Proje Kalıcılığı](../../extensibility/internals/project-persistence.md)  
 `IPersistFileFormat`Hem dosya hem de dosya tabanlı olmayan proje nesnelerini kalıcı hale getirmek için kullanımını açıklar.  
  
 [MSBuild Kullanma](../../extensibility/internals/using-msbuild.md)  
 Proje tipinin, [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] kullanıcıların [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , komut satırından ve ' den derlenmesi için yapı altyapısını nasıl kullanabilecebileceğinizi açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Sembol Tarama Araçlarını Destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 **Nesne tarayıcısı** ve **sınıf görünümü** penceresi gibi kod görüntüleme araçlarının mimarisini açıklar. VSPackage 'ta nesne taramayı uygulamak için kullanılan arabirimleri ve yöntemleri açıklar.  
  
 [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Proje öğesi açıldığında ve proje kaynaklarının nasıl işlenebileceği hakkında hangi düzenleyicinin kullanıldığını belirlemek için projelerin oynadığı önemi açıklar.  
  
 [Windows Installer ile VSPackage Yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 VSPackage 'un kendi benzersiz kimliği ve bir Windows Installer paketindeki VSPackage dll 'larınızı ve diğer bilgileri nasıl sarılacağını gösterir (. MSI dosyası) müşterilere dağıtım için.  
  
 [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Görünümlerin ve adreslerin hiyerarşilerini açıklar.  
  
 [VSPackage’lar](../../extensibility/internals/vspackages.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Ortamı genişleten ve kendi VSPackage 'ı nasıl uygulayacağınızı ele alan, yüklenebilen BIR com nesnesi olan VSPackage 'a genel bir bakış sağlar.  
  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Kodu değiştirmek, kod derlemek ve derlemek ve kodu çalıştırmak ve hata ayıklamak için projelerin nasıl kullanılacağını açıklar ve proje türlerinin nasıl oluşturulacağı hakkında ayrıntılı konulara bağlantılar sağlar.
