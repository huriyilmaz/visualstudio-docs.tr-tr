---
title: Önbellek verileri
description: verilerin çevrimdışı olarak veya Microsoft Office kelime veya Excel açılmadan veya açmadan veri nesnelerini bir belge düzeyi özelleştirmesinde nasıl önbelleğe alabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 547c2be11a2c52baf7d5d2c7d3ac1be4b06ed5999d3bb16e3e626c37ba3eed9b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384554"
---
# <a name="cache-data"></a>Önbellek verileri
  verilerin çevrimdışı olarak erişilebilmesi veya Microsoft Office kelime ya da Microsoft Office Excel açılmadan, veri nesnelerini belge düzeyi özelleştirmesinde önbelleğe alabilirsiniz. Bir nesneyi önbelleğe almak için, nesnenin belirli gereksinimleri karşılayan bir veri türü olması gerekir. .NET Framework birçok ortak veri türü,, ve dahil olmak üzere bu gereksinimleri karşılar <xref:System.String> <xref:System.Data.DataSet> <xref:System.Data.DataTable> .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Veri önbelleğine bir nesne eklemenin iki yolu vardır:

- Çözüm oluşturulduğunda veri önbelleğine bir nesne eklemek için <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliği nesne bildirimine uygulayın. Daha fazla bilgi için bkz. [nasıl yapılır: çevrimdışı kullanım için verileri önbelleğe alma veya bir sunucu üzerinde](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Çalışma zamanında veri önbelleğine program aracılığıyla bir nesne eklemek için, `StartCaching` veya sınıfları gibi bir konak öğesinin yöntemini kullanın `ThisDocument` `ThisWorkbook` . daha fazla bilgi için bkz. [nasıl yapılır: program aracılığıyla bir veri kaynağını bir Office belgesinde önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

  Veri önbelleğine bir nesne ekledikten sonra, Word veya Excel başlatmadan önbelleğe alınmış verilere erişebilir ve değişiklik yapabilirsiniz. Daha fazla bilgi için bkz. [sunucudaki belgelerdeki verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Önbelleğe alınacak veri nesneleri için gereksinimler
 Çözümünüzde bir veri nesnesini önbelleğe almak için, nesnenin şu gereksinimleri karşılaması gerekir:

- Veya sınıfları gibi bir konak öğesinin okuma/yazma ortak alanı veya özelliği olun `ThisDocument` `ThisWorkbook` .

- Bir Dizin Oluşturucu veya başka parametreli bir özellik değil.

  Ayrıca, veri nesnesi sınıf tarafından seri hale getirilebilir olmalıdır <xref:System.Xml.Serialization.XmlSerializer> , bu da nesnenin türünün bu özelliklere sahip olması anlamına gelir:

- Ortak bir tür olun.

- Parametresi olmayan ortak bir oluşturucuya sahip.

- Ek güvenlik ayrıcalıkları gerektiren kodu yürütmüyor.

- Yalnızca okuma/yazma genel özelliklerini kullanıma sunma (diğer özellikler yok sayılır).

- Çok boyutlu dizileri kullanıma sunmuyor (iç içe diziler kabul edilir).

- Özelliklerden ve alanlardan arabirimler döndürmez.

- <xref:System.Collections.IDictionary>Bir koleksiyon ise uygulamaz.

  Bir veri nesnesini önbelleğe aldığınızda, nesne, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] belgedeki *özel bir XML bölümünde* depolanan bir XML dizesinde seri hale getirir. Daha fazla bilgi için bkz. [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).

## <a name="cached-data-size-limits"></a>Önbelleğe alınmış veri boyutu sınırları
 Belgedeki veri önbelleğine ekleyebileceğiniz toplam veri miktarına yönelik bazı sınırlar vardır ve veri önbelleğindeki her bir nesnenin boyutu. Bu sınırları aşarsanız, veri veri önbelleğine kaydedildiğinde uygulama beklenmedik şekilde kapatılabilir.

 Bu limitlerden kaçınmak için şu yönergeleri izleyin:

- Veri önbelleğine 10 MB 'tan daha büyük bir nesne eklemeyin.

- Tek bir belgedeki veri önbelleğine 100 MB 'tan fazla veri eklemeyin.

  Bunlar yaklaşık değerlerdir. Tam sınırlar, kullanılabilir RAM ve çalışan işlem sayısı dahil olmak üzere çeşitli etkenlere bağlıdır.

## <a name="control-the-behavior-of-cached-objects"></a>Önbelleğe alınmış nesnelerin davranışını denetleme
 Önbelleğe alınmış bir nesnenin davranışı üzerinde daha fazla denetim kazanmak için <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> arabirimini önbelleğe alınmış nesnenin türüne uygulayabilirsiniz. Örneğin, nesne değiştirildiğinde kullanıcının nasıl bildirileceğini denetlemek istiyorsanız bu arabirimi uygulayabilirsiniz. nasıl uygulanacağını gösteren kod örnekleri için <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> , `ControlCollection` [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)içindeki dinamik denetimler örneği ve Word dinamik denetimleri örneği Excel.

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Parola korumalı belgelerde önbelleğe alınmış verilerde yapılan değişiklikleri kalıcı hale getirme
 Bir parolayla korunan bir belgedeki veri nesnelerini önbelleğe alırsanız, önbelleğe alınmış verilerde yapılan değişiklikler kaydedilmez. Önbelleğe alınmış verilere yapılan değişiklikleri iki yöntemi geçersiz kılarak kaydedebilirsiniz. Belge kaydedildiğinde korumayı geçici olarak kaldırmak için bu yöntemleri geçersiz kılın ve Kaydet işlemi tamamlandıktan sonra korumayı yeniden uygulayın.

 Daha fazla bilgi için bkz. [nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md).

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Veri önbelleğine null değerler eklenirken veri kaybını önleme
 Veri önbelleğine nesne eklediğinizde, belge kaydedilmeden ve kapatılmadan önce önbelleğe alınmış nesnelerin tümünün **null** olmayan bir değere başlatılması gerekir. Önbelleğe alınan herhangi bir nesne, belge kaydedilip kapatıldığında **null** değere sahipse, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] önbelleğe alınan tüm nesneleri veri önbelleğinden otomatik olarak kaldırır.

 Tasarım zamanında özniteliğini kullanarak veri önbelleğine **null** değeri olan bir nesne eklerseniz <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> , <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> belge açılmadan önce önbelleğe alınmış veri nesnelerini başlatmak için sınıfını kullanabilirsiniz. belge son kullanıcı tarafından açılmadan önce, Word veya Excel yüklü olmayan bir sunucuda önbelleğe alınmış verileri başlatmak istiyorsanız bu kullanışlıdır. Daha fazla bilgi için bkz. [sunucudaki belgelerdeki verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: çevrimdışı veya sunucuda kullanmak üzere verileri önbelleğe alma](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [nasıl yapılır: bir Office belgesinde program aracılığıyla veri kaynağını önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [İzlenecek yol: önbelleğe alınmış bir veri kümesini kullanarak ana ayrıntı ilişkisi oluşturma](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
