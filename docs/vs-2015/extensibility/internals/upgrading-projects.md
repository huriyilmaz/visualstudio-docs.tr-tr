---
title: Projeleri yükseltme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787218"
---
# <a name="upgrading-projects"></a>Projeleri Yükseltme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir sürümünden diğerine proje modelinde yapılan değişiklikler, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] daha yeni sürümde çalıştırılabilmesi için projelerin ve çözümlerin yükseltilmesini gerektirebilir. , [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Kendi projelerinizde yükseltme desteğini uygulamak için kullanılabilen arabirimler sağlar.  
  
## <a name="upgrade-strategies"></a>Yükseltme stratejileri  
 Bir yükseltmeyi desteklemek için, proje sistemi uygulamanızın bir yükseltme stratejisi tanımlayıp uygulaması gerekir. Stratejinizi belirlemek için yan yana (SxS) yedeklemeyi, kopya yedeklemesini veya her ikisini de desteklemeyi seçebilirsiniz.  
  
- SxS yedekleme, bir projenin yalnızca yükseltilmesi gereken dosyaları, örneğin ". old" gibi uygun bir dosya adı sonekini ekleyerek kopyaladığını gösterir.  
  
- Kopya yedekleme, bir projenin tüm proje öğelerini Kullanıcı tarafından belirtilen bir yedekleme konumuna kopyaladığı anlamına gelir. Özgün proje konumundaki ilgili dosyalar yükseltilir.  
  
## <a name="how-upgrade-works"></a>Yükseltme nasıl Işe yarar?  
 Önceki bir sürümünde oluşturulan bir çözüm [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] daha yeni bir sürümde AÇıLDıĞıNDA IDE, yükseltilmesi gerekip gerekmediğini öğrenmek için çözüm dosyasını denetler. Yükseltme gerekliyse, yükseltme **Sihirbazı** , kullanıcıya yükseltme işlemi boyunca yol gösterecek şekilde otomatik olarak başlatılır.  
  
 Bir çözümün yükseltilmesi gerektiğinde, her proje fabrikasını yükseltme stratejisi için sorgular. Strateji, proje fabrikasının kopya yedeklemesini mi yoksa SxS yedeklemesini mi desteklediğini belirler. Bilgiler, yedekleme için gereken bilgileri toplayan ve Kullanıcı için geçerli seçenekleri sunan **Yükseltme Sihirbazına**gönderilir.  
  
### <a name="multi-project-solutions"></a>Çoklu proje çözümleri  
 Bir çözüm birden çok proje içeriyorsa ve yükseltme stratejileri farklıysa (örneğin, yalnızca SxS yedeklemesini destekleyen bir C++ projesi ve yalnızca kopya yedeklemesini destekleyen bir Web projesi gibi), proje fabrikaları yükseltme stratejisi üzerinde anlaşmalıdır.  
  
 Çözüm her proje fabrikasını sorgular <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Daha sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> , genel proje dosyalarının yükseltilmesi gerekip gerekmediğini ve desteklenen yükseltme stratejilerini belirlemesini sağlamak için çağırır. **Yükseltme Sihirbazı** daha sonra çağrılır.  
  
 Kullanıcı Sihirbazı tamamladıktan sonra, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> gerçek yükseltmeyi gerçekleştirmek için her proje fabrikası üzerinde çağırılır. Backup 'ı kolaylaştırmak için IVsProjectUpgradeViaFactory yöntemleri, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> yükseltme işleminin ayrıntılarını günlüğe kaydetmek için hizmeti sağlar. Bu hizmet önbelleğe alınamaz.  
  
 Tüm ilgili genel dosyalar güncelleştirildikten sonra her proje fabrikası bir proje örneğini oluşturmayı seçebilirler. Proje uygulamasının desteklemesi gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Daha sonra tüm ilgili proje öğelerini yükseltmek için yöntemi çağırılır.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>Yöntemi, Svsupgradegünlükçü hizmetini sağlamaz. Bu hizmet çağırarak elde edilebilir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>En İyi Uygulamalar  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>Düzenlemeden önce bir dosyayı düzenleyip düzenleyebiliyorsanız ve kaydetmeden önce bu hizmeti kaydedebilir. Bu, yedekleme ve yükseltme uygulamalarınızın, kaynak denetimi altındaki proje dosyalarını, yetersiz izinlere sahip dosyaları ve benzerlerini işlemesini yardımcı olur.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>Yükseltme işleminin başarısı veya başarısızlığı hakkında bilgi sağlamak için yedekleme ve yükseltme aşamaları sırasında hizmeti kullanın.  
  
 Projeleri yedekleme ve yükseltme hakkında daha fazla bilgi için, vsshell2. IDL içindeki IVsProjectUpgrade için açıklamalara bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeyle](../../extensibility/internals/projects.md)   
 [Özel projeleri yükseltme](../../misc/upgrading-custom-projects.md)   
 [Proje öğeleri yükseltiliyor](../../misc/upgrading-project-items.md)
