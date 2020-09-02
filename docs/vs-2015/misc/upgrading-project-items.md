---
title: Proje öğeleri yükseltiliyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698691"
---
# <a name="upgrading-project-items"></a>Proje öğeleri yükseltiliyor
Uygulamadıysanız proje sistemleri içine öğe ekler veya bunları yönetiyorsanız, proje yükseltme işlemine katılmanız gerekebilir. Crystal Reports, proje sistemine eklenebilecek bir öğe örneğidir.  
  
 Genellikle proje öğesi uygulayıcıları, proje başvurularının ne olduğunu ve başka proje özelliklerinin yükseltme kararı vermek için ne olduğunu bilmeleri gerektiğinden, zaten tam olarak örneklenen ve yükseltilen bir projeden yararlanmak istiyor.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Proje yükseltme bildirimini almak için  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>Proje öğesi uygulamanızda bayrağını ayarlayın (vsshell80. IDL içinde tanımlanmıştır). Bu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kabuk bir proje sisteminin yükseltme sürecinde olduğunu belirlediğinde, proje öğesi VSPackage 'ın otomatik olarak yüklenmesine neden olur.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>Yöntemi aracılığıyla arabirime tavsiye edin <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> .  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>Arabirim, proje sistemi uygulamasının yükseltme işlemlerini tamamladıktan sonra yeni yükseltilen proje oluşturulduktan sonra tetiklenir. Senaryoya bağlı olarak, arabirim,, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> veya yöntemlerinden sonra tetiklenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> .  
  
### <a name="to-upgrade-the-project-item-files"></a>Proje öğesi dosyalarını yükseltmek için  
  
1. Dosya yedekleme sürecini proje öğesi uygulamanızda dikkatle yönetmeniz gerekir. Bu, yöntemin parametresinin olarak ayarlandığı, bir yan yana yedekleme için geçerlidir. burada, `fUpgradeFlag` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> yedeklenen dosyalar ". old" olarak belirlenmiş olan dosyaların yanına yerleştirilir. Projenin yükseltilme sırasında sistem saatinden daha eski olan yedeklenen dosyalar eski olarak belirlenebilir. Ayrıca, bunu engellemek için özel adımlar yapmadığınız takdirde bunların üzerine yazılabilir.  
  
2. Proje öğesi proje yükseltmesinin bir bildirimini aldığında, **Visual Studio Dönüştürme Sihirbazı** yine de görüntülenir. Bu nedenle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Sihirbaz kullanıcı arabirimine yükseltme iletileri sağlamak için arabirimin yöntemlerini kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Dönüştürme Sihirbazı](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Özel projeleri yükseltme](../misc/upgrading-custom-projects.md)