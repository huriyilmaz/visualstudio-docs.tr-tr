---
title: 'Nasıl yapılır: başarısız proje yükseltmeleriyle Ilgili sorunları giderme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 65059e285777e48633da5eb7e8723e3997f37dfa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844446"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Nasıl Yapılır: Başarısız Visual Studio Proje Yükseltmelerinde Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazen Visual Studio, bir projeyi daha önceki bir sürümünden tamamen dönüştüremiyor [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Aşağıdaki bölümlerde yer alan ipuçları belirli bir sorunu gidermezse TechNet [wiki: geliştirme portalı](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio)hakkında daha fazla bilgi bulabilirsiniz.

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Dosyalar bulunamadığı için proje çalışmıyor
 Proje dosyası [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , F5 tuşuna bastığınızda projeyi çalıştırmak için kullanan sabit kodlanmış dosya yollarını içerir. Bu yollarda devenv.exe ve diğer gerekli dosyaların konumu bulunabilir. Uygulamasının yükseltilen bir sürümünde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bu dosyaların yolları değiştirilmiş olabilir.

#### <a name="to-resolve-incorrect-file-paths"></a>Hatalı dosya yollarını çözümlemek için

1. Proje dosyanızı bir metin düzenleyicisinde açın.

2. Yanlış olabilecek, özellikle de sürüm numarası içeren dosya yollarını tarayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

3. Hatalı dosya yollarını yeni hedeflere işaret eden şekilde değiştirin.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Başvurular geçerli olmadığından proje derlenmiyor
 Yükselttiğinizde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , sürümünü de yükseltmeniz de gerekebilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Projeniz yeni sürümde kullanımdan kaldırılmıştır başvurular içeriyorsa [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , doğru çözümlenmeyebilir. Bu özellikle, örneğin, sürüm numaralarını içeren başvurular için olasıdır `Microsoft.VisualStudio.Shell.Interop.8.0` .

 Kodunuzun çok sayıda geçersiz başvurusu varsa en kolay çözüm, uygulamasının [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] önceki bir sürümünü hedeflemek için Çoklu hedefleme özelliğini kullanmak olabilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

#### <a name="to-resolve-incorrect-references"></a>Hatalı başvuruları çözümlemek için

1. Proje dosyanızı bir metin düzenleyicisinde açın.

2. Proje özelliklerini açın.

3. Doğru **hedef çerçeve** değerini seçin. Alternatif olarak, `<TargetFrameworkVersion>` öğesinin değerini proje dosyasında doğrudan değiştirebilirsiniz.

   Projenizin yükseltilen sürümde çalışmasını istiyorsanız, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] projenin başvurularını güncelleştirmeniz ve ayrıca `Imports` başvuruları çağıran tüm ya da deyimleri güncelleştirmeniz gerekir `Using` . Projeniz IDE 'de yüklenirse, **Çözüm Gezgini** veya **başvuru Yöneticisi** iletişim kutusunu kullanarak başvuruları güncelleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [/Upgrade (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [ASP.NET 4 ' e dönüştürülüyor](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
