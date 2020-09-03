---
title: VSPackages için Otomasyon sağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6eb76eba76567f2966323d4058c9e752cb6fb69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200978"
---
# <a name="providing-automation-for-vspackages"></a>VSPackage’lar için Otomasyon Sağlama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackages için Otomasyon sağlamanın iki ana yolu vardır: VSPackage 'a özgü nesneler uygulayarak ve standart otomasyon nesnelerini uygulayarak. Genellikle, bu, ortamın otomasyon modelini genişletmek için birlikte kullanılır.  
  
## <a name="vspackage-specific-objects"></a>VSPackage 'a özgü nesneler  
 Otomasyon modeli içindeki belirli konumlar, VSPackage için benzersiz olan Otomasyon nesneleri sağlamanızı gerektirir. Örneğin, yeni projeler yalnızca VSPackage 'un sağladığı ayrı nesneler gerektirir. Bu nesnelerin adları kayıt defterine girilir ve ortam nesnesine çağrılar aracılığıyla elde edilir `DTE` .  
  
 Bir Otomasyon tüketicisi standart bir nesnenin Object özelliği aracılığıyla sağlanmış nesneyi kullandığında VSPackage 'a özgü nesneler de elde edilebilir. Örneğin, standart nesne, `Window` `Object` genellikle özelliği olarak bilinen bir özelliğine sahiptir `Windows.Object` . Tüketiciler `Window.Object` VSPackage 'da uygulanan bir pencerede öğesini çağırdıklarında, kendi tasarımınızın belirli bir Otomasyon nesnesini geri geçitirsiniz.  
  
#### <a name="projects"></a>Projeler  
 VSPackages, yeni proje türleri için otomasyon modelini kendi VSPackage 'a özgü nesneler aracılığıyla genişletebilir. VSPackage için yeni otomasyon nesneleri sağlamanın birincil amacı, benzersiz proje nesnelerinizi bir veya nesnesinden ayırt edesağlamaktır <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> <xref:VSLangProj80.VSProject2> . Bu fark, proje türünü diğer proje türlerinden ayrı olarak bir veya tekrarlamak için bir yöntem sağlamak istediğinizde yararlı olur ve bir çözümde yan yana görünmeleri gerekir. Daha fazla bilgi için bkz. [Proje nesnelerini gösterme](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Ekinlikler  
 Ortamın olay mimarisi, kendi VSPackage 'a özgü nesnelerinizi eklemek için başka bir yer sunar. Örneğin, kendi benzersiz olay nesnelerinizi oluşturarak ortamın olay modelini projeler için genişletebilirsiniz. Kendi proje türüne yeni bir öğe eklendiğinde kendi olaylarınızı sağlamak isteyebilirsiniz. Daha fazla bilgi için bkz. [olayları gösterme](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Pencere Nesneleri  
 Windows, çağrıldığında VSPackage 'a özgü bir Otomasyon nesnesini bir ortama geri geçirebilir. İçinden türetilmiş bir nesne <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> veya `IDispatch` geri dönüş özellikleri, onun bulunduğu pencere nesnesini genişleterek uygulanır. Örneğin, bir pencere çerçevesinde bir denetim için Otomasyon sağlamak üzere bu yaklaşımı kullanabilirsiniz. Bu nesnenin semantiğinin ve genişletebileceğini diğer nesnelerin tasarımı sizin için tasarlanmıştır. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Otomasyonu sağlama](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Araçlar menüsündeki Seçenekler sayfası  
 Araçlar, Seçenekler otomasyon modelini sayfaları uygulayarak ve kendi seçeneklerinizi oluşturmak için kayıt defterine bilgi ekleyerek araçlar, Seçenekler otomasyon modeli ' ni genişletmek için sayfalar oluşturabilirsiniz. Sayfalarınız daha sonra diğer seçenek sayfaları gibi ortam nesne modeli aracılığıyla çağrılabilir. Ortama, VSPackages aracılığıyla eklemek istediğiniz özelliğin tasarımı seçenek sayfaları gerektiriyorsa, Otomasyon desteğini de eklemeniz gerekir. Daha fazla bilgi için bkz. [Seçenekler sayfaları Için Otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Standart Otomasyon nesneleri  
 Projelere yönelik Otomasyonu genişletmek için, diğer proje nesnelerinin yanında bulunan standart otomasyon nesnelerini (öğesinden türetilmiş) de uygular `IDispatch` ve standart yöntemler ve özellikler uygular. Standart nesne örnekleri,,, ve gibi çözüm hiyerarşisine eklenen proje nesnelerini içerir `Projects` `Project` `ProjectItem` `ProjectItems` . Her yeni proje türü, bu nesneleri (ve büyük olasılıkla projenizin semantiklerine bağlı olarak diğer olanları) uygulamalıdır.  
  
 Bu nesneler bir anlamda, VSPackage 'a özgü proje nesnelerinin karşıt avantajlarından yararlanır. Standart Otomasyon nesneleri, projenizin aynı nesneleri destekleyen diğer projeler gibi Genelleştirilmiş bir şekilde kullanılmasını sağlar. Bu nedenle, genel ve nesnelere karşı yazılmış bir eklenti `Project` herhangi bir `ProjectItem` türdeki projelere göre işlev görebilir. Daha fazla bilgi için bkz. [Proje modelleme](../../extensibility/internals/project-modeling.md).
