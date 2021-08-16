---
title: Office çözümlerini yükseltme ve geçirme
description: Visual Studio önceki bir sürümünde oluşturulmuş bir Offince projeniz varsa, projeyi Visual Studio güncel sürümlerinde kullanmak üzere yükseltmeniz gerekir.
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
ms.openlocfilehash: af09d705ddeb0fdbf01244ee085d93fb54d52ac7969c8e1e6de9917abc32b431
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384151"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Office çözümlerini yükseltme ve geçirme
  Visual Studio önceki bir sürümünde oluşturulmuş bir Microsoft Office projeniz varsa, projeyi Visual Studio güncel sürümlerinde kullanmak üzere yükseltmeniz gerekir. Microsoft Office bir projeyi yükseltmek için, uygulamayı Microsoft Office geliştirici araçlarını içeren bir Visual Studio sürümünde açın. Microsoft Office geliştirici araçlarını içeren Visual Studio sürümleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio, Visual Studio önceki sürümleri kullanılarak oluşturulan ınfopath form şablonu projelerini yükseltemez. Bu tür projeler geçerli Visual Studio sürümünde desteklenmez.

## <a name="changes-to-upgraded-projects"></a>Yükseltilen projelere yapılan değişiklikler
 bir Microsoft Office projesi yükselttiğinizde, Visual Studio projeyi aşağıdaki öğeleri hedefleyecek şekilde değiştirir:

- Office çalışma zamanına yönelik Visual Studio 2010 araçları. daha fazla bilgi için bkz. [Office için Visual Studio Araçları çalışma zamanına genel bakış](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Geçerli derleme başvuruları.

- proje türü tarafından desteklenen .NET Framework sürümü (yalnızca Visual Studio 2013 sürümüne yükselttiğinizde).

- proje türü tarafından desteklenen Microsoft Office sürümü (yalnızca Visual Studio 2013 sürümüne yükselttiğinizde).

## <a name="assembly-references"></a>Bütünleştirilmiş kod başvuruları
 Visual Studio, projedeki aşağıdaki derleme başvurularını yükseltir:

- Microsoft Office birincil birlikte çalışma derlemeleri (pıa).

- İçindeki derlemeler [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . bu derlemeler hakkında daha fazla bilgi için bkz. [Office için Visual Studio Araçları çalışma zamanına genel bakış](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Bağımlı derlemelerin yeni veya güncelleştirilmiş sürümleri.

## <a name="targeted-net-framework"></a>Hedeflenen .NET Framework
 bir projeyi Visual Studio 2013 yükselttiğinizde, Visual Studio ya da öğesini hedeflemek için projeyi değiştirir [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . projenin hedeflediği .net framework sürümü, bilgisayarınızda hangi Office sürümünün yüklü olduğuna bağlıdır. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]yüklüyse, öğesini hedeflemek için projeyi değiştirir Visual Studio [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . aksi takdirde, Visual Studio hedeflemek için projeyi değiştirir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

> [!NOTE]
> Geliştirme ve son kullanıcı bilgisayarlarında yeniden hedeflenmiş bir çözüm çalıştırmak için bazı ek adımlar gerçekleştirmeniz gerekebilir ve projeniz, belirli özellikleri kullanıyorsa, artık derlenmeyecektir. daha fazla bilgi için bkz. [.NET Framework 4 veya sonraki sürümlere Office çözümleri geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]bir Office projesinde veya üstünü hedefliyorsanız, .NET Framework 3,5 ' i hedeflediğinizde kullanılamayan bazı özellikleri kullanabilirsiniz. daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>hedeflenen Office uygulaması
 bir Office projesini Visual Studio 2013 sürümüne yükselttiğinizde Visual Studio proje, belge düzeyi özelleştirme projesi veya VSTO eklenti projesi gibi proje türü tarafından desteklenen Microsoft Office sürümünü hedeflemek için projeyi değiştirir.

 Visual Studio 2013 Office projeler hedefleyebilir [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamalar. Visual Studio, yüklediğiniz office 'in en son sürümünü hedeflemek için projeyi değiştirir. bu Office sürümlerinden hiçbiri yüklü değilse, Visual Studio projeyi yükseltmez.

> [!NOTE]
> hedef veya daha sonraki bir VSTO eklenti projesini yükseltirseniz [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] , `ThisAddIn_Startup` VSTO eklentisinin olay işleyicisinin uygulamadaki bir belgeye erişen bir kod içermediğinden emin olun. daha fazla bilgi için bkz. [Office uygulaması başladığında belgeye erişme](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 belge düzeyi özelleştirmeleri için, bir [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] projedeki bir *.xls* veya *.doc* uzantısı olan belgeler gibi ikili biçime sahip belgeleri Office açık XML biçimine dönüştürür. Open XML hakkında daha fazla bilgi için bkz. [yeni dosya adı uzantılarına giriş ve açık XML biçimleri](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> akıllı etiketler Excel 2010 ve Word 2010 ' de kullanım dışıdır. bu nedenle, çözümünüz akıllı etiketler kullanıyorsa, Visual Studio 2013 veya Visual Studio 2015 ' de test etmeden ve hata ayıklamadan önce bunları kaldırmanız gerekir.

## <a name="upgrade-microsoft-office-2003-projects"></a>Microsoft Office 2003 projelerini yükseltin
 belge düzeyi özelleştirmelerini yükseltmek için bazı ek konular ve Microsoft Office 2003 ' i hedefleyen VSTO eklentileri vardır.

### <a name="document-level-projects"></a>Belge düzeyi projeleri
 projedeki belge Windows Forms denetimleri içeriyorsa, projeyi yükseltmeden önce Office ikinci sürüm çalışma zamanı için Visual Studio 2005 araçlarının de yüklü olması gerekir. Projeyi yükseltmeden önce çalışma zamanının bu sürümü geliştirme bilgisayarında yüklü değilse, yükseltilen proje derleme veya çalıştırma zamanı hataları içerebilir. projeyi yükseltmeyi tamamladıktan sonra, başka bir Office çözümü tarafından kullanılmıyorsa, Office ikinci sürüm çalışma zamanı için Visual Studio 2005 araçlarını geliştirme bilgisayarından kaldırabilirsiniz. çalışma zamanının bu sürümü, [Office ikinci sürüm çalışma zamanı (VSTO 2005 SE) (x86) için Microsoft Visual Studio 2005 araçlarında](https://www.microsoft.com/download/details.aspx?id=2392)Microsoft indirme merkezi 'nden yeniden dağıtılabilir bir paket olarak sunulmaktadır.

### <a name="vsto-add-in-projects"></a>VSTO Eklenti projeleri
 özgün projeniz için çözüm dosyası VSTO eklentisini yüklemek üzere yapılandırılmış bir kurulum veya ınstallshield Limited Edition projesi içeriyorsa Visual Studio projeyi yükseltir, ancak projede başka bir değişiklik yapmaz. VSTO eklentisini dağıtmak için bir Windows Installer dosyası kullanmaya devam etmek istiyorsanız, kurulum veya ınstallshield Limited Edition projesini, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Office çalışma zamanı için Visual Studio 2010 araçları ve isteğe bağlı olarak VSTO eklentisinin başvurduğu birincil birlikte çalışma derlemelerini yüklemek üzere değiştirmelisiniz. daha fazla bilgi için bkz. [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 VSTO eklentiyi dağıtmak için ClickOnce kullanmak istiyorsanız, kurulum veya ınstallshield Limited Edition projesini tamamen silebilirsiniz. ClickOnce kullanarak VSTO eklentileri dağıtma hakkında daha fazla bilgi için bkz. [Office çözümü dağıtma](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: Office çözümlerini yükseltme](/previous-versions/4bez6837(v=vs.140))
- [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Project Yükseltme, Seçenekler iletişim kutusu](../vsto/project-upgrade-options-dialog-box.md)