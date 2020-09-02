---
title: Sihirbazlar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e58ebd736f7bb9f35df6e41d5235f36f7037259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687625"
---
# <a name="wizards"></a>Sihirbazlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sihirbaz oluşturduktan sonra, genellikle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] başkalarının kullanabilmesi için tümleşik geliştirme ortamına (IDE) eklemek istersiniz. Eklenen sihirbaz daha sonra **Yeni Proje Ekle** veya **Yeni öğe Ekle** iletişim kutularında görünür. **Yeni Proje Ekle** veya **Yeni öğe Ekle** iletişim kutularını görmek için **Çözüm Gezgini**bir açık çözüme sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni proje** veya **Yeni öğe**' ye tıklayın.  
  
 Sihirbazlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , kullanıcıların **Yeni Proje Ekle** Iletişim kutusunu veya **Yeni öğe Ekle** iletişim kutusunu açtıklarında veya **Çözüm Gezgini**bir öğeye sağ tıkladıklarında kullanılabilir değerlerin ağaç görünümünden seçim yapmasına olanak sağlamak için ' de uygulanabilir.  
  
 Sihirbazda, yeni bir proje ya da ITES adını yerelleştirme seçeneğini belirtebilir ve kullanıcıların Sihirbazı seçerken göreceği simgeyi belirleyebilirsiniz. Ayrıca, yeni öğelerin kullanılabilir diğer öğelere göre görünme sırasını da denetleyebilirsiniz; öğelerin alfabetik olarak organize olması gerekmez.  
  
 Ayrıca, açıldığında sihirbaza geçirilen özel parametrelere dayalı olarak, farklı şekilde başlayan bir sihirbaz da sağlayabilirsiniz.  
  
 Bu bölümdeki konularda, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Yeni Proje Ekle** ve **Yeni öğe Ekle** iletişim kutularının, sihirbazın kullanılabilir sihirbazlar ve şablonlar arasında ve sihirbazın IDE 'de doğru şekilde çalışması için karşılaması gereken gereksinimler hakkında tartışın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Şablon dizin açıklama dosyalarına genel bir bakış sağlar ve iletişim kutularındaki bir projeyle ilişkili klasörleri, sihirbaz. vsz dosyalarını ve şablon dosyalarını görüntüleme, IDE 'de nasıl çalıştığını açıklar.  
  
 [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)  
 IDE 'nin sihirbazları nasıl başlattığı ve. vsz dosyasının üç parçasını listeleyen açıklanır.  
  
 [Sihirbaz Arabirimi (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 `IDTWizard`SIHIRBAZLARıN IDE 'de çalışmak için uygulaması gereken arabirimi açıklar.  
  
 [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md)  
 Sihirbazların nasıl uygulandığını ve IDE 'nin uygulamaya bağlam parametrelerini geçirdiğinde ne olduğunu açıklar.  
  
 [Özel Parametreler](../../extensibility/internals/custom-parameters.md)  
 Sihirbaz başlatıldıktan sonra sihirbazın işlemini denetlemek için özel parametrelerin nasıl kullanılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Yeni proje türlerinin nasıl tasarlanabileceği hakkında bilgi sunan ek konuların bağlantılarını sağlar.  
  
 [İzlenecek yol: sihirbaz oluşturma](https://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Bir sihirbazın nasıl oluşturulacağını gösterir.  
  
 [Projeleri Genişletme](../../extensibility/extending-projects.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Kod dosyalarını ve kaynak dosyalarını düzenlemek için projelerin ve çözümlerin nasıl kullanılacağını ve kaynak denetiminin nasıl uygulanacağını açıklar.
