---
title: Office çözümlerini yükseltme ve geçirme
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e421d6e4ee94d9974c0a0583db1fb495c72593e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79416542"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Office çözümlerini yükseltme ve geçirme
  Visual Studio 'nun önceki bir sürümünde oluşturulmuş bir Microsoft Office projeniz varsa, projeyi Visual Studio 'nun geçerli sürümlerinde kullanmak üzere yükseltmeniz gerekir. Microsoft Office bir projeyi yükseltmek için, Microsoft Office geliştirici araçlarını içeren bir Visual Studio sürümünde açın. Microsoft Office geliştirici araçlarını içeren Visual Studio sürümleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio, Visual Studio 'nun önceki sürümleri kullanılarak oluşturulan InfoPath form şablonu projelerini yükseltemez. Bu tür projeler Visual Studio 'nun geçerli sürümünde desteklenmez.

## <a name="changes-to-upgraded-projects"></a>Yükseltilen projelere yapılan değişiklikler
 Bir Microsoft Office projesini yükselttiğinizde, Visual Studio projeyi aşağıdaki öğeleri hedefleyecek şekilde değiştirir:

- Office çalışma zamanı için Visual Studio 2010 araçları. Daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Geçerli derleme başvuruları.

- Proje türü tarafından desteklenen .NET Framework sürümü (yalnızca Visual Studio 2013 sürümüne yükselttiğinizde).

- Proje türü tarafından desteklenen Microsoft Office sürümü (yalnızca Visual Studio 2013 sürümüne yükselttiğinizde).

## <a name="assembly-references"></a>Bütünleştirilmiş kod başvuruları
 Visual Studio, projede aşağıdaki derleme başvurularını yükseltir:

- Microsoft Office birincil birlikte çalışma derlemeleri (PIA).

- İçindeki derlemeler [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Bu derlemeler hakkında daha fazla bilgi için, bkz. [Office çalışma zamanına genel bakış Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Bağımlı derlemelerin yeni veya güncelleştirilmiş sürümleri.

## <a name="targeted-net-framework"></a>Hedeflenen .NET Framework
 Bir projeyi Visual Studio 2013 yükselttiğinizde, Visual Studio, ya da öğesini hedeflemek için projeyi değiştirir [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Projenin hedeflediği .NET Framework sürümü, bilgisayarınızda yüklü olan Office sürümüne göre değişir. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]Yüklüyse, Visual Studio öğesini hedeflemek için projeyi değiştirir [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Aksi halde, Visual Studio, hedeflemek için projeyi değiştirir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

> [!NOTE]
> Geliştirme ve son kullanıcı bilgisayarlarında yeniden hedeflenmiş bir çözüm çalıştırmak için bazı ek adımlar gerçekleştirmeniz gerekebilir ve projeniz, belirli özellikleri kullanıyorsa, artık derlenmeyecektir. Daha fazla bilgi için bkz. [Office çözümlerini .NET Framework 4 veya sonraki bir sürüme geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Office projesinde veya üstünü hedefliyorsanız, .NET Framework 3,5 ' i hedeflediğinizde kullanılamayan bazı özellikleri kullanabilirsiniz. Daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Hedeflenen Office uygulaması
 Bir Office projesini Visual Studio 2013 yükselttiğinizde, Visual Studio projeyi bir belge düzeyi özelleştirme projesi veya VSTO eklenti projesi gibi proje türü tarafından desteklenen Microsoft Office bir sürümü hedefleyecek şekilde değiştirir.

 Visual Studio 2013 Office projeleri hedefleyebilir [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamalar. Visual Studio, yüklediğiniz Office 'in en son sürümünü hedeflemek için projeyi değiştirir. Bu Office sürümlerinden hiçbiri yüklü değilse, Visual Studio projeyi yükseltmez.

> [!NOTE]
> Hedef veya daha sonra bir VSTO eklenti projesini yükseltirseniz [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] , `ThisAddIn_Startup` VSTO eklentisinin olay işleyicisinin uygulamadaki bir belgeye erişen bir kod içermediğinden emin olun. Daha fazla bilgi için bkz. [Office uygulaması başladığında belgeye erişme](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Belge düzeyi özelleştirmeleri için, bir [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] *. xls* veya *. doc* uzantılı belgeler gibi ikili biçime sahip BIR projedeki belgeleri Office Open XML biçimine dönüştürür. Open XML hakkında daha fazla bilgi için bkz. [yeni dosya adı uzantılarına giriş ve açık XML biçimleri](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> Akıllı Etiketler Excel 2010 ve Word 2010 ' de kullanımdan kaldırılmıştır. Bu nedenle, çözümünüz Akıllı Etiketler kullanıyorsa, Visual Studio 2013 veya Visual Studio 2015 ' de test etmeden ve hata ayıklamadan önce bunları kaldırmanız gerekir.

## <a name="upgrade-microsoft-office-2003-projects"></a>Microsoft Office 2003 projelerini yükseltin
 Microsoft Office 2003 ' i hedefleyen belge düzeyi özelleştirmelerini ve VSTO Eklentilerini yükseltmek için bazı ek hususlar vardır.

### <a name="document-level-projects"></a>Belge düzeyi projeleri
 Projedeki belge Windows Forms denetimleri içeriyorsa, projeyi yükseltmeden önce Office Ikinci sürüm çalışma zamanı için Visual Studio 2005 Araçları ' nı da yüklemiş olmanız gerekir. Projeyi yükseltmeden önce çalışma zamanının bu sürümü geliştirme bilgisayarında yüklü değilse, yükseltilen proje derleme veya çalıştırma zamanı hataları içerebilir. Projeyi yükseltmeyi tamamladıktan sonra, diğer Office çözümleri tarafından kullanılmıyorsa Office Second Edition çalışma zamanı için Visual Studio 2005 araçları 'nı geliştirme bilgisayarından kaldırabilirsiniz. Çalışma zamanının bu sürümü, [Office Ikinci sürüm çalışma zamanı (VSTO 2005 de) (x86) için Microsoft Visual Studio 2005 araçlarında](https://www.microsoft.com/download/details.aspx?id=2392)Microsoft İndirme Merkezi 'nden yeniden dağıtılabilir bir paket olarak sunulmaktadır.

### <a name="vsto-add-in-projects"></a>VSTO eklenti projeleri
 Özgün projeniz için çözüm dosyası, VSTO eklentisini yüklemek üzere yapılandırılmış bir kurulum veya InstallShield Limited Edition projesi içeriyorsa, Visual Studio projeyi yükseltir, ancak projede başka bir değişiklik yapmaz. VSTO eklentisini dağıtmak için bir Windows Installer dosyası kullanmaya devam etmek istiyorsanız, kurulum veya InstallShield Limited Edition projesini, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Office çalışma zamanı Için Visual Studio 2010 araçları ve isteğe bağlı olarak VSTO eklentisi tarafından başvurulan birincil birlikte çalışma derlemelerini yüklemek üzere değiştirmeniz gerekir. Daha fazla bilgi için bkz. [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 VSTO eklentisini dağıtmak için ClickOnce kullanmak istiyorsanız, kurulum veya InstallShield Limited Edition projesini tamamen silebilirsiniz. VSTO Eklentilerini ClickOnce kullanarak dağıtma hakkında daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Office çözümlerini yükseltme](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Proje yükseltme, Seçenekler iletişim kutusu](../vsto/project-upgrade-options-dialog-box.md)
