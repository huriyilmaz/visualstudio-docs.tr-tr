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
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416542"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Office çözümlerini yükseltme ve geçirme
  Visual Studio'nun önceki bir sürümünde oluşturulmuş bir Microsoft Office projeniz varsa, projeyi Visual Studio'nun geçerli sürümlerinde kullanmak üzere yükseltmeniz gerekir. Bir Microsoft Office projesini yükseltmek için, Visual Studio'nun Microsoft Office geliştirici araçlarını içeren bir sürümünde açın. Visual Studio'nun Microsoft Office geliştirici araçlarını içeren sürümleri hakkında daha fazla bilgi için [bkz.](../vsto/configuring-a-computer-to-develop-office-solutions.md)

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio, Visual Studio'nun önceki sürümlerini kullanarak oluşturulan InfoPath form şablon projelerini yükseltemez. Bu tür projeler Visual Studio'nun geçerli sürümünde desteklenmez.

## <a name="changes-to-upgraded-projects"></a>Yükseltilen projelerde yapılan değişiklikler
 Bir Microsoft Office projesini yükselttiğinde, Visual Studio projeyi aşağıdaki öğeleri hedef alacak şekilde değiştirir:

- Visual Studio 2010 Office çalışma zamanı için araçlar. Daha fazla bilgi [için, Office çalışma zamanı genel bakışı için Visual Studio Araçları'na](../vsto/visual-studio-tools-for-office-runtime-overview.md)bakın.

- Geçerli derleme başvuruları.

- .NET Framework'ün proje türü tarafından desteklenen bir sürümü (yalnızca Visual Studio 2013'e yükselttiğinde).

- Microsoft Office'in proje türütarafından desteklenen bir sürümü (yalnızca Visual Studio 2013'e yükselttiğinde).

## <a name="assembly-references"></a>Montaj başvuruları
 Visual Studio projedeki aşağıdaki montaj başvurularını yükseltir:

- Microsoft Office birincil interop derlemeleri (PIA).

- Meclisler [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]içinde . Bu derlemeler hakkında daha fazla bilgi için [Office çalışma süresine genel bakış için Visual Studio Araçları'na](../vsto/visual-studio-tools-for-office-runtime-overview.md)bakın.

- Bağımlı derlemelerin yeni veya güncelleştirilmiş sürümleri.

## <a name="targeted-net-framework"></a>Hedeflenen .NET Çerçevesi
 Visual Studio 2013'e bir proje yükselttiğinde, Visual Studio projeyi 'yi [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] veya [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Proje tarafından hedeflenen .NET çerçevesinin sürümü, Office'in bilgisayarınıza hangi sürümünün yüklendiğinden bağlıdır. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] Yüklenirse, Visual Studio projeyi '' [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]yi hedeflemek için değiştirir. Aksi takdirde, Visual Studio hedef projeyi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]değiştirir.

> [!NOTE]
> Geliştirme ve son kullanıcı bilgisayarlarında yeniden hedeflenen bir çözümü çalıştırmak için bazı ek adımlar gerçekleştirmeniz gerekebilir ve projeniz belirli özellikler kullanıyorsa artık derlenmez. Daha fazla bilgi için [bkz.](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)

 Bir Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] projesini veya daha sonrasını hedefliyorsanız, .NET Framework 3.5'i hedeflediğinizde kullanılamayan bazı özellikleri kullanabilirsiniz. Daha fazla bilgi için [Tasarım'a](../vsto/designing-and-creating-office-solutions.md)bakın ve Office çözümleri oluşturun.

## <a name="targeted-office-application"></a>Hedeflenen Ofis uygulaması
 Bir Office projesini Visual Studio 2013'e yükselttiğinde Visual Studio, projeyi Microsoft Office'in belge düzeyinde özelleştirme projesi veya VSTO Eklenti projesi gibi proje türü tarafından desteklenen bir sürümünü hedefleyecek şekilde değiştirir.

 Visual Studio 2013'teki [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] Office [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] projeleri ve uygulamaları hedefleyebilir. Visual Studio, yüklediğiniz ofisin en son sürümünü hedeflemek için projeyi değiştirir. Office'in bu sürümlerinden hiçbiri yüklenmiyorsa, Visual Studio projeyi yükseltmez.

> [!NOTE]
> Bir VSTO Eklenti projesini hedeflemek [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] veya daha sonra yükseltmek `ThisAddIn_Startup` için yükseltirseniz, VSTO Eklentisi'nin olay işleyicisinin uygulamada belgeye erişen kod içermediğinden emin olun. Daha fazla bilgi [için, Office uygulaması başladığında belgeye eriş'e](../vsto/programming-vsto-add-ins.md#AccessingDocuments)bakın.

 Belge düzeyinde özelleştirmeler [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] için, *.xls* veya *.doc* uzantılı belgeler gibi ikili biçimi olan bir projedeki belgeleri Office Open XML biçimine dönüştürür. Açık XML hakkında daha fazla bilgi [için, yeni dosya adı uzantılarına giriş ve XML biçimlerini açın'a](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1)bakın.

> [!NOTE]
> Akıllı etiketler Excel 2010 ve Word 2010'da amortismana alınır. Bu nedenle, çözümünüz akıllı etiketler kullanıyorsa, Visual Studio 2013 veya Visual Studio 2015'te test edip hata ayıklamadan önce bunları kaldırmanız gerekir.

## <a name="upgrade-microsoft-office-2003-projects"></a>Microsoft Office 2003 projelerini yükseltme
 Microsoft Office 2003'ü hedefleyen belge düzeyindeözelleştirmeleri ve VSTO Eklentilerini yükseltmek için bazı ek noktalar vardır.

### <a name="document-level-projects"></a>Belge düzeyinde projeler
 Projedeki belge Windows Forms denetimleri içeriyorsa, projeyi yükseltmeden önce Visual Studio 2005 Office İkinci Sürüm Çalıştırma Zamanı Için Araçlar yüklü olmalıdır. Projeyi yükseltmeden önce çalışma zamanının bu sürümü geliştirme bilgisayarında yüklenmezse, yükseltilen proje derleme veya çalıştırma zamanı hataları içerebilir. Projeyi yükseltmeyi tamamladıktan sonra, diğer Office çözümleri tarafından kullanılmadığı takdirde Visual Studio 2005 Office İkinci Sürüm Çalışma Süresi Araçlarını geliştirme bilgisayarından kaldırabilirsiniz. Çalışma zamanının bu sürümü, [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392)adresindeki Microsoft Download Center'dan yeniden dağıtılabilir paket olarak kullanılabilir.

### <a name="vsto-add-in-projects"></a>VSTO Eklenti projeleri
 Özgün projenizin çözüm dosyasında VSTO Eklentisini yüklemek üzere yapılandırılan bir Kurulum veya InstallShield Limited Edition projesi varsa, Visual Studio projeyi yükseltir, ancak projede başka bir değişiklik yapmaz. VSTO Eklentinizi dağıtmak için bir Windows Installer dosyasını kullanmaya devam etmek istiyorsanız, Office Runtime için Visual Studio 2010 Tools ve isteğe bağlı olarak VSTO Eklentiniz tarafından başvurulan birincil interop derlemeleri gibi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]yeni ön koşulları yüklemek için Kurulum veya InstallShield Limited Edition projesini değiştirmeniz gerekir. Daha fazla bilgi için bkz. Windows [Installer'ı kullanarak Bir Office çözümlerini dağıtın.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

 VSTO Eklentinizi dağıtmak için ClickOnce'yi kullanmak istiyorsanız, Kurulum veya InstallShield Limited Edition projesini tamamen silebilirsiniz. ClickOnce'i kullanarak VSTO Eklentilerini dağıtma hakkında daha fazla bilgi [için](../vsto/deploying-an-office-solution.md)bkz.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Office çözümlerini yükseltme](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [Office çözümlerini .NET Framework 4 veya sonraki lere geçirin](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Proje Yükseltme, Seçenekler iletişim kutusu](../vsto/project-upgrade-options-dialog-box.md)
