---
title: 'Nasıl yapılır: başarısız proje yükseltmelerinde sorun giderme | Microsoft Docs'
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
ms.openlocfilehash: 16232a72cd37f8d1d68760f032b6050e0bdf74c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300360"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Nasıl Yapılır: Başarısız Visual Studio Proje Yükseltmelerinde Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazen Visual Studio, bir projeyi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]önceki bir sürümünden tamamen dönüştüremiyor. Aşağıdaki bölümlerde yer alan ipuçları belirli bir sorunu gidermezse TechNet [wiki: geliştirme portalı](https://go.microsoft.com/fwlink/?LinkId=254808)hakkında daha fazla bilgi bulabilirsiniz.

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Proje dosyaları bulunamadı çünkü çalışmaz
 Proje dosyası, F5 tuşuna bastığınızda projeyi çalıştırmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], sabit kodlanmış dosya yollarını içerir. Bu yolları konumunu devenv.exe ve diğer gerekli dosyaları içerebilir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]yükseltilen bir sürümünde, bu dosyaların yolları değiştirilmiş olabilir.

#### <a name="to-resolve-incorrect-file-paths"></a>Hatalı dosya yollarını çözmek için

1. Proje dosyanız, bir metin düzenleyicisinde açın.

2. Yanlış olabilecek, özellikle de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürüm numarası içeren dosya yollarını tarayın.

3. Hatalı dosya yolları yeni hedefe işaret edecek şekilde değiştirin.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Proje başvuruları geçerli olmadığından oluşturmuyor
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]yükselttiğinizde [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünü de yükseltmeniz de gerekebilir. Projeniz yeni [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünde kullanımdan kaldırılmıştır başvurular içeriyorsa, doğru çözümlenmeyebilir. Bu, özellikle de `Microsoft.VisualStudio.Shell.Interop.8.0`sürüm numaraları içeren başvurular için olasıdır.

 Kodunuzun çok sayıda geçersiz başvurusu varsa, en kolay çözüm, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]daha önceki bir sürümünü hedeflemek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Çoklu hedefleme özelliğini kullanmak olabilir.

#### <a name="to-resolve-incorrect-references"></a>Yanlış başvurularını çözümlemek için

1. Proje dosyanız, bir metin düzenleyicisinde açın.

2. Proje özelliklerini açın.

3. Doğru **hedef çerçeve** değerini seçin. Alternatif olarak, proje dosyasında `<TargetFrameworkVersion>` öğesinin değerini doğrudan değiştirebilirsiniz.

   Projenizin yükseltilen [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümünde çalışmasını istiyorsanız, projenin başvurularını güncelleştirmeniz ve ayrıca başvuruları çağıran tüm `Imports` veya `Using` deyimlerini güncelleştirmeniz gerekir. Projeniz IDE 'de yüklenirse, **Çözüm Gezgini** veya **başvuru Yöneticisi** iletişim kutusunu kullanarak başvuruları güncelleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [/Upgrade (devenv. exe)](../ide/reference/upgrade-devenv-exe.md) [ASP.NET 4 ' e dönüştürülüyor](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
