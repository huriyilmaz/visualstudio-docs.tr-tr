---
title: Çözümlerini yükseltme Office geçirme
description: Visual Studio'nin önceki bir sürümünde oluşturulmuş bir Office projeniz varsa projeyi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0acbd41096ea7a234155b6bbee69800480c41674
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431672"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Çözümlerini yükseltme Office geçirme
  Visual Studio önceki bir sürümünde oluşturulmuş bir Microsoft Office projeniz varsa, projeyi geçerli Visual Studio sürümlerinde kullanmak için yükseltmeniz gerekir. Bir Microsoft Office yükseltmek için, projeyi geliştirici araçlarını içeren Visual Studio sürümünü Microsoft Office açın. Geliştirici araçlarını içeren Visual Studio sürümleri hakkında daha fazla bilgi Microsoft Office için, bkz. Bir bilgisayarı Office [geliştirme.](../vsto/configuring-a-computer-to-develop-office-solutions.md)

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio, önceki sürümleri kullanılarak oluşturulan InfoPath form şablonu projelerini Visual Studio. Bu tür projeler, geçerli sürümde Visual Studio.

## <a name="changes-to-upgraded-projects"></a>Yükseltilen projelerde yapılan değişiklikler
 Bir Microsoft Office yükseltin, Visual Studio aşağıdaki öğeleri hedefleyeceksiniz:

- Çalışma Visual Studio için Office 2010 Araçları. Daha fazla bilgi için bkz. [Office için Visual Studio Araçları genel bakış.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

- Geçerli derleme başvuruları.

- Proje türü tarafından desteklenen .NET Framework bir sürüm (Yalnızca Visual Studio 2013' sürümüne yükseltin).

- Proje türü Microsoft Office desteklenen bir sürüm (Yalnızca bir sürüme Visual Studio 2013).

## <a name="assembly-references"></a>Derleme başvuruları
 Visual Studio, projede aşağıdaki derleme başvurularını yükselter:

- Microsoft Office birlikte çalışma derlemelerini (PIA) kullanabilirsiniz.

- içinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derlemeler. Bu derlemeler hakkında daha fazla bilgi için bkz. [Office için Visual Studio Araçları genel bakış.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

- Bağımlı derlemelerin yeni veya güncelleştirilmiş sürümleri.

## <a name="targeted-net-framework"></a>Hedeflenen .NET Framework
 Bir projeyi bir Visual Studio 2013 Visual Studio veya hedefini [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] hedefleyeceksiniz. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Proje tarafından hedeflenen .NET Framework sürümü, bilgisayarınızda yüklü Office sürümüne bağlıdır. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]yüklüyse, Visual Studio hedefini hedefleyeceksiniz. [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] Aksi Visual Studio hedefini hedefleyeceksiniz. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

> [!NOTE]
> Geliştirme ve son kullanıcı bilgisayarlarında yeniden hedeflenmiş bir çözüm çalıştırmak için bazı ek adımlar gerçekleştirmeniz gerekebilirsiniz ve projeniz belirli özellikleri kullanıyorsa artık derlemeyecektir. Daha fazla bilgi için [bkz. Office 4 veya sonraki bir .NET Framework](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)geçirme.

 Bir Office projesinde veya sonraki bir hedefiniz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] varsa, 3.5'i hedefleye .NET Framework bazı özellikleri kullanabilirsiniz. Daha fazla bilgi için, [bkz. Tasarım ve Office çözümleri.](../vsto/designing-and-creating-office-solutions.md)

## <a name="targeted-office-application"></a>Hedeflenen Office uygulaması
 Office projesini Visual Studio 2013'ye yükselterek Visual Studio, belge düzeyi özelleştirme projesi veya VSTO Eklenti projesi gibi proje türü tarafından desteklenen Microsoft Office sürümünü hedeflemek için projeyi değiştiren bir uygulamadır.

 Office projeleri Visual Studio 2013 uygulamaları [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] hedefleyene. Visual Studio, projeyi, yüklü office'in en son sürümünü hedefleyeceksiniz. Bu sürümlerden hiçbiri Office yüklüyse, Visual Studio projeyi yükseltmez.

> [!NOTE]
> VSTO Eklenti projesini hedef veya sonraki bir sürümüne yükseltersiniz, VSTO Eklentisinde olay işleyicinin uygulama içinde bir belgeye erişen kod içermey olduğundan [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] `ThisAddIn_Startup` emin olun. Daha fazla bilgi için [bkz. Uygulama başlatıldığında Office erişme.](../vsto/programming-vsto-add-ins.md#AccessingDocuments)

 Belge düzeyinde özelleştirmeler için,.xlsveya.docuzantısına sahip belgeler gibi ikili biçime sahip bir projede yer alan belgeleri Açık [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] XML biçimine Office dönüştürür.   Open XML hakkında daha fazla bilgi için [bkz. Yeni dosya adı uzantılarına ve Open XML biçimlerine giriş.](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1)

> [!NOTE]
> Akıllı etiketler 2010 ve Word 2010'Excel kullanım dışıdır. Bu nedenle, çözümünüz akıllı etiketler kullanıyorsa, 2015'te veya 2015'te Visual Studio 2013 veya Visual Studio kaldırmanız gerekir.

## <a name="upgrade-microsoft-office-2003-projects"></a>2003 Microsoft Office yükseltme
 2003'ü hedef alan belge düzeyi özelleştirmeleri ve VSTO yükseltme konusunda dikkat edilmesi gereken Microsoft Office vardır.

### <a name="document-level-projects"></a>Belge düzeyi projeler
 Proje içinde belge Windows Forms denetimleri içeriyorsa, projeyi yükseltmeden önce Visual Studio 2005 Office İkinci Sürüm Çalışma Zamanı için de yüklü olmalıdır. Projeyi yükseltmeden önce çalışma zamanının bu sürümü geliştirme bilgisayarına yüklenmemişse, yükseltilen proje derleme veya çalışma zamanı hataları içerebilir. Projeyi yükseltmeyi bitirdikten sonra, Visual Studio 2005 Tools for Office Second Edition Runtime'ı geliştirme bilgisayarından kaldırabilirsiniz. Bu, başka bir Office çözümü tarafından kullanılmamaktadır. Çalışma zamanının bu sürümü, Office İkinci Sürüm Çalışma Zamanı (VSTO 2005 SE) (x86) için Microsoft Visual Studio 2005 Araçları'nda Microsoft İndirme Merkezi'nden yeniden dağıtılabilir bir paket olarak kullanılabilir.

### <a name="vsto-add-in-projects"></a>VSTO Eklenti projeleri
 Özgün projenizin çözüm dosyasında VSTO Eklentisini yüklemek için yapılandırılmış bir Kurulum veya InstallShield Limited Edition projesi varsa Visual Studio projeyi yükseltse de projede başka bir değişiklik yapmaz. VSTO Eklentinizi dağıtmak için bir Windows Yükleyici dosyası kullanmaya devam etmek için Kurulum veya InstallShield Limited Edition projesini, Office Çalışma Zamanı için Visual Studio 2010 Araçları ve isteğe bağlı olarak VSTO Eklentiniz tarafından başvurulan birincil birlikte çalışma derlemeleri gibi yeni önkulları yüklemek için değiştirmeniz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gerekir. Daha fazla bilgi için [bkz. Office Yükleyicisi kullanarak bir Windows dağıtma.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

 ClickOnce Eklentinizi dağıtmak için VSTO kullanmak için Kurulum veya InstallShield Limited Edition projesini tamamen silebilirsiniz. ClickOnce kullanarak VSTO hakkında daha fazla bilgi için bkz. Office [dağıtma.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Office: Office yükseltme](/previous-versions/4bez6837(v=vs.140))
- [Office çözümlerini 4 veya .NET Framework'ye geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Project Yükseltme, Seçenekler iletişim kutusu](../vsto/project-upgrade-options-dialog-box.md)