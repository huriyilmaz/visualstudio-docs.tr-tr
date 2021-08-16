---
title: Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler
description: Verilerin Visual Studio veri önbelleği olarak katıştırma özelliğini etkinleştirerek belge düzeyi özelleştirmelerde verilerin görünümden nasıl ayrımlı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cac4ed52e82664fd5aca2fd4e924f24b3eb68e58e18cd6142db9c7c236af35be
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384593"
---
# <a name="cached-data-in-document-level-customizations"></a>Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler
  Belge düzeyinde özelleştirmelerin birincil amacı, belgelerde verileri görünümden Office etmektir. Veriler, sayılar ve metinler de dahil olmak üzere belgede depolanan bilgileri ifade eder. Görünüm, Word ve Microsoft Office kullanıcı arabirimini ve nesne modelini Microsoft Office Excel.

 Visual Studio, verilerin veri önbelleği olarak da adlandırılan bir veri adası *olarak* ekleştirilmesini sağlayarak belge düzeyinde özelleştirmeler görünümünden verileri *birbirinden ayırıyor.* Word veya Excel' başlatmadan verileri doğrudan okuyabilir veya Excel. Bu, yüklü bir sunucuya sahip değil bir sunucu üzerinde belgelerde verileri değiştirmeniz Microsoft Office yararlıdır. Sözcük ve Excel istemci ortamlarında kullanılmak üzere tasarlanmıştır; bir sunucuda çalıştıracak şekilde tasarlanmamalarını sağlar.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Belge düzeyinde özelleştirmeler hakkında daha fazla bilgi için [bkz. Office](../vsto/office-solutions-development-overview-vsto.md) çözüm geliştirmeye genel bakış &#40;VSTO&#41;ve Belge düzeyi [özelleştirmelerin mimarisi.](../vsto/architecture-of-document-level-customizations.md)

## <a name="understand-the-cached-data-programming-model"></a>Önbelleğe alınmış veri programlama modelini anlama
 Veri adası, çözümünüzde belirli gereksinimleri karşılayacak herhangi bir nesne içerebilir. Bu nesneler <xref:System.Data.DataSet> nesneleri, <xref:System.Data.DataTable> nesneleri ve sınıfı tarafından seri hale getirilecek diğer nesneleri <xref:System.Xml.Serialization.XmlSerializer> içerir. Daha fazla bilgi için [bkz. Verileri önbelleğe alın.](../vsto/caching-data.md)

 Önbelleğe alınan verilerin görünümünü sağlamak için belgedeki Windows Forms  denetimlerini ve konak denetimlerini veri adası nesnelerine bekleyebilirsiniz. Veri adası ile veriye bağlı denetimler arasındaki veri bağlaması, iki verinin eşitlenmiş durumda tutar. Denetimlerden bağımsız olan verilere doğrulama kodu da ekebilirsiniz. Daha fazla bilgi için [bkz. Veri bağlama çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

 Konak denetimleri, Excel ve Word nesne modellerinde yerel nesnelerin genişletilmiş sürümleridir. Yerel nesnelerin aksine, konak denetimleri doğrudan yönetilen veri nesnelerine bağlanabilirsiniz. Daha fazla bilgi için [bkz. Konak öğelerine ve konak denetimlerine genel](../vsto/host-items-and-host-controls-overview.md) bakış [Windows form denetimlerine Office genel bakış.](../vsto/windows-forms-controls-on-office-documents-overview.md)

## <a name="access-cached-data-on-the-server"></a>Sunucuda önbelleğe alınmış verilere erişme
 Bir belgede önbelleğe alınmış verilere erişmek için sınıfını <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> kullanabilirsiniz. Bu sınıf , 'nin bir parçasıdır ve word veya [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Word çalıştırmadan Excel kullanılabilir. Önbelleğe alınan verileri değiştirdikten sonra kullanıcı belgeyi açtığında, verilere bağlı tüm denetimler değişikliklerle otomatik olarak eşitlenir ve kullanıcıya güncelleştirilmiş veriler açılır. Daha fazla bilgi için [bkz. sunucusundaki belgelerde verilere erişme.](../vsto/accessing-data-in-documents-on-the-server.md)

 Excel ve Word'in sunucu verilerine yazması gerekmez, yalnızca istemcide görüntülemek için gereklidir. Excel ve Word'in sunucuda yüklü olması bile gerek değildir. Bu, geliştirilmiş ölçeklenebilirlik ve veri adalarını içeren belgelerin hızlı toplu işlemesini gerçekleştirme olanağı sağlar.

## <a name="data-caching-for-offline-use"></a>Çevrimdışı kullanım için veri önbelleğe alma
 Verilerin veri adasına depolanması çevrimdışı senaryolara olanak sağlar. Kullanıcı bir belgeyi ilk kez açtığında veya sunucudan belgeyi isterken veri adası en son verilerle doldurulur. Veri adası belgede önbelleğe alınmış ve çevrimdışı olarak kullanılabilir. Canlı bağlantı mevcut olsa bile kullanıcı (ve kodunuz) verileri işleyene kadar kullanabilir. Kullanıcı yeniden bağlandığında, verilerde yapılan değişiklikler sunucu veri kaynağına geri yayabilirsiniz.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Önbelleğe alınan veriler ve özel XML bölümleri karşılaştırması
 Özel XML parçaları, 2007 Microsoft Office xml parçalarını bir belgede depolamanın bir yolu olarak tanıtıldı. Özel XML bölümleri veri önbelleğiyle aynı senaryoların çoğunda yararlı olsa da, veri adası ile özel XML bölümleri arasında bazı farklar vardır. Özel XML bölümleri hakkında daha fazla bilgi için bkz. [Özel XML parçalarına genel bakış.](../vsto/custom-xml-parts-overview.md)

 Aşağıdaki tabloda bazı farklar ve benzerlikler listelemektedir.

|Soru / Özellik|Veri önbelleği|Özel XML bölümleri|
|-|----------------|----------------------|
|Hangi Office uygulamaları bunları kullanabilir?|Aşağıdaki uygulamalar için belge düzeyinde özelleştirmeler:<br /><br /> - Excel<br />- Word|Aşağıdaki uygulamalar için belge düzeyi ve uygulama düzeyinde çözümler:<br /><br /> - Excel<br />- PowerPoint<br />- Word|
|Ne tür verileri depolarsınız?|Özelleştirme derlemenizin belirli gereksinimlerine uygun herhangi bir genel nesne. Daha fazla bilgi için [bkz. Verileri önbelleğe alın.](../vsto/caching-data.md)|Herhangi bir XML verisi.|
|Uygulamalara başlamadan verilere Microsoft Office?|Evet, tarafından sağlanan <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfını [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kullanarak.|Evet, ad alanı sınıflarını <xref:System.IO.Packaging> veya Open XML Biçim SDK'sı kullanarak.|

## <a name="see-also"></a>Ayrıca bkz.
- [Veri Office verileri](../vsto/data-in-office-solutions.md)
- [Office çözüm mimarisi Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
