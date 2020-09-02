---
title: .NET Framework Hedefleme hatalarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ae55e34f929acca6c708dfc39477f3bd6546f53f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703779"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>.NET Framework Hedefleme Hatalarının Sorunlarını Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, başvuru sorunları ve bu hataları nasıl giderebileceğinizi belirten MSBuild hataları açıklanmaktadır.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>.NET Framework farklı bir sürümünü hedefleyen bir proje veya derlemeye başvurmuş olabilirsiniz  
 Farklı sürümlerini hedefleyen projelere veya derlemelere başvuran uygulamalar oluşturabilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Örneğin, için istemci profilini hedefleyen bir uygulama oluşturabilir, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ancak .NET Framework 2,0 ' i hedefleyen bir derlemeye başvuru yapabilirsiniz. Ancak, daha önceki bir sürümünü hedefleyen bir proje oluşturursanız, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Bu projedeki bir başvuruyu veya kendisi için istemci profilini hedefleyen bir proje ya da derlemeye ayarlayamazsınız [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] . Hatayı gidermek için uygulamanızın, uygulamanızın başvurduğu projeler veya derlemeler tarafından hedeflenen profille uyumlu bir profili veya profilleri hedeflediğinden emin olun.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Bir projeyi .NET Framework farklı bir sürümüne yeniden hedeflediniz  
 Uygulamanız için uygulamasının hedef sürümünü değiştirirseniz, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Visual Studio bazı başvuruları değiştirir ancak bazı başvuruları el ile güncelleştirmeniz gerekebilir. Örneğin, bir uygulamayı hedefleyecek şekilde değiştirirseniz [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] ve bu uygulamanın, için istemci profilini kullanan kaynakları veya ayarları varsa, daha önce bahsedilen hatalardan biri meydana gelebilir [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] .  
  
 Uygulama ayarlarını geçici olarak çözmek için **Çözüm Gezgini**açın, **tüm dosyaları göster**' i seçin ve sonra Visual Studio 'nun XML düzenleyicisinde app.config dosyasını düzenleyin. Ayarlarınızdaki sürümü .NET Framework uygun sürümüyle eşleşecek şekilde değiştirin. Örneğin, 4.0.0.0 olan sürüm ayarını 2.0.0.0 olarak değiştirebilirsiniz. Benzer şekilde, kaynakları ekleyen bir uygulama için **Çözüm Gezgini**açın, **tüm dosyaları göster** düğmesini seçin, **projem** (Visual Basic) veya **Özellikler** (C#) öğesini genişletin ve ardından Visual Studio 'nun XML düzenleyicisinde resources. resx dosyasını düzenleyin. 4.0.0.0 olan sürüm ayarını 2.0.0.0 olarak değiştirin.  
  
 Uygulamanızın simgeler veya bit eşlemler veya veri bağlantı dizeleri gibi ayarlar gibi kaynakları varsa, **Proje Tasarımcısı** 'nın **Ayarlar** sayfasındaki tüm öğeleri kaldırarak ve ardından gerekli ayarları yeniden ekleyerek hatayı çözebilirsiniz.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Bir projeyi .NET Framework farklı bir sürümüne yeniden hedeflediniz ve başvurular çözümlenmiyor  
 Bir projeyi farklı bir sürümüne yeniden hedeflemeniz durumunda [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , başvurularınız bazı durumlarda düzgün şekilde çözümlenmeyebilir. Derlemelere yönelik açık tam başvurular genellikle bu soruna neden olur, ancak çözümlenmez olan başvuruları kaldırarak ve ardından projeye geri ekleyerek çözümü çözebilirsiniz. Alternatif olarak, başvuruları değiştirmek için proje dosyasını düzenleyebilirsiniz. İlk olarak, aşağıdaki formun başvurularını kaldırırsınız:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Daha sonra bunları basit formla değiştirirsiniz:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
> Projenizi kapatıp yeniden açtıktan sonra tüm başvuruların doğru şekilde çözümlendiğinden emin olmak için yeniden oluşturmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework Istemci profili](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Çoklu sürüm desteği](../msbuild/msbuild-multitargeting-overview.md)
