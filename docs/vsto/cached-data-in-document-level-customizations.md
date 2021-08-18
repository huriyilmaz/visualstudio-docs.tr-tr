---
title: Belge düzeyi Özelleştirmelerdeki önbelleğe alınmış veriler
description: verilerin veri önbelleği olarak katıştırılması için verileri belge düzeyi özelleştirmelerine göre Visual Studio nasıl ayıran hakkında bilgi edinin.
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
ms.openlocfilehash: 528e452142bbac81654a6f55878265ee544ddb39
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083745"
---
# <a name="cached-data-in-document-level-customizations"></a>Belge düzeyi Özelleştirmelerdeki önbelleğe alınmış veriler
  belge düzeyi özelleştirmelerinin birincil amacı, verileri Office belgelerdeki görünümden ayıramaktır. Veriler, belgede saklanan, sayılar ve metin gibi bilgileri ifade eder. görünüm, kullanıcı arabirimine ve Microsoft Office Word ve Microsoft Office Excel nesne modeline başvurur.

 Visual Studio, verilerin veri *önbelleği* olarak da adlandırılan bir *veri adası* olarak gömülmesini sağlayarak belge düzeyi özelleştirmelerde görünümden verileri ayırır. Word veya Excel başlatmadan verileri doğrudan okuyabilir veya değiştirebilirsiniz. bu, Microsoft Office yüklü olmayan bir sunucudaki belgelerdeki verileri değiştirmeniz gerektiğinde faydalıdır. Word ve Excel, istemci ortamlarında kullanılmak üzere tasarlanmıştır; Bunlar bir sunucuda çalıştırılmak üzere tasarlanmamıştır.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 belge düzeyi özelleştirmeleri hakkında daha fazla bilgi için bkz. [Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) ve [belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>Önbelleğe alınmış veri programlama modelini anlama
 Veri Adası, çözümünüzde belirli gereksinimleri karşılayan herhangi bir nesneyi içerebilir. Bu nesneler <xref:System.Data.DataSet> nesne, <xref:System.Data.DataTable> nesne ve sınıf tarafından seri hale getirilebilen diğer nesneleri içerir <xref:System.Xml.Serialization.XmlSerializer> . Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).

 önbelleğe alınmış verilerin görünümünü sağlamak için, belgedeki Windows Forms denetimleri ve *konak denetimlerini* veri adasındaki nesnelere bağlayabilirsiniz. Veri Adası ve veri bağlama denetimleri arasında veri bağlama, iki eşitlenme yapmaz. Ayrıca, denetimlerden bağımsız verilere doğrulama kodu ekleyebilirsiniz. daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

 konak denetimleri, Excel ve Word nesne modellerinde yerel nesnelerin genişletilmiş sürümleridir. Yerel nesnelerden farklı olarak, konak denetimleri doğrudan yönetilen veri nesnelerine bağlanabilir. daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md) ve [Office belgelere genel bakış Windows Forms denetimleri](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="access-cached-data-on-the-server"></a>Sunucuda önbelleğe alınmış verilere erişin
 Bir belgedeki önbelleğe alınmış verilere erişmek için <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfını kullanabilirsiniz. bu sınıf, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ' ın bir parçasıdır ve Excel veya Word 'ü çalıştırmadan bir sunucuda kullanılabilir. Önbelleğe alınmış verileri değiştirdikten sonra Kullanıcı belgeyi açtığında, verilere bağlanan denetimler otomatik olarak değişikliklerle eşitlenir ve Kullanıcı güncelleştirilmiş verilerle birlikte sunulur. Daha fazla bilgi için bkz. [sunucudaki belgelerdeki verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).

 Excel ve Word 'ün yalnızca istemcide görüntülemek için, sunucudaki verilere yazılması gerekmez. Excel ve Word 'ün sunucuda yüklü olması da gerekmez. Bu, geliştirilmiş ölçeklenebilirlik ve veri Adaları içeren belgelerin hızlı toplu işlem işlemlerini gerçekleştirme yeteneği sağlar.

## <a name="data-caching-for-offline-use"></a>Çevrimdışı kullanım için veri önbelleğe alma
 Veri adasında verilerin depolanması, çevrimdışı senaryolara izin vermez. Bir Kullanıcı bir belgeyi ilk açtığında veya belgeyi sunucudan istediğinde, veri Adası en son verilerle doldurulur. Veri Adası belgede önbelleğe alınır ve daha sonra çevrimdışı olarak kullanılabilir. Kullanıcı (ve kodunuz), canlı bağlantı kullanılabilir olmasa bile verileri işleyebilir. Kullanıcı yeniden bağlandığında, verilerdeki değişiklikler sunucu veri kaynağına geri yayılamaz.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Önbelleğe alınan veriler ve özel XML bölümleri karşılaştırması
 özel xml bölümleri, bir belgede rastgele xml parçalarını depolamanın bir yolu olarak 2007 Microsoft Office sisteminde tanıtılmıştı. Özel XML parçaları veri önbelleğiyle aynı senaryoların çoğunda yararlı olsa da, veri Adası ve özel XML bölümleri arasında bazı farklılıklar vardır. Özel XML bölümleri hakkında daha fazla bilgi için bkz. [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).

 Aşağıdaki tabloda bazı farklılıklar ve benzerlikler listelenmektedir.

|Soru/Özellik|Veri önbelleği|Özel XML bölümleri|
|-|----------------|----------------------|
|hangi Office uygulamalar bunları kullanabilir?|Aşağıdaki uygulamalar için belge düzeyi özelleştirmeleri:<br /><br /> -Excel<br />-Sözcük|Aşağıdaki uygulamalar için belge düzeyi ve uygulama düzeyi çözümler:<br /><br /> -Excel<br />-PowerPoint<br />-Sözcük|
|Hangi veri türlerini depolayabilmeniz gerekir?|Özelleştirme derlemenizin belirli gereksinimleri karşılayan herhangi bir ortak nesne. Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).|Herhangi bir XML verisi.|
|Microsoft Office uygulamaları başlatmadan verilere erişebilirsiniz miyim?|Evet, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> tarafından sağlanmış sınıfını kullanarak [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|Evet, <xref:System.IO.Packaging> ad alanındaki sınıfları veya Open XML biçimi SDK 'sını kullanarak.|

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde veri](../vsto/data-in-office-solutions.md)
- [Visual Studio Office çözümlerin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
