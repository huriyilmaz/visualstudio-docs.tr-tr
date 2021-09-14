---
title: Önbellek verileri
description: Verilere çevrimdışı olarak veya Word veya Microsoft Office açmadan erişilebilir olması için belge düzeyinde bir özelleştirmede veri nesnelerini Excel.
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
ms.openlocfilehash: f8779089fc4987d600f3860151782d0322f9d1fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635446"
---
# <a name="cache-data"></a>Önbellek verileri
  Verilere çevrimdışı olarak veya Word veya Microsoft Office açmadan erişilebilen bir belge düzeyi özelleştirmesinde veri nesnelerini Microsoft Office Excel. Bir nesneyi önbelleğe alan nesnenin belirli gereksinimleri karşılayacak bir veri türüne sahip olması gerekir. , ve dahil olmak üzere .NET Framework çoğu yaygın veri türü bu <xref:System.String> gereksinimleri <xref:System.Data.DataSet> <xref:System.Data.DataTable> karşılar.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Veri önbelleğine nesne eklemenin iki yolu vardır:

- Çözüm yerleşik olduğunda veri önbelleğine bir nesnesi eklemek için <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliğini nesne bildirimine ekleyin. Daha fazla bilgi için [bkz. Nasıl kullanılır: Verileri çevrimdışı veya bir sunucuda kullanmak üzere önbelleğe alın.](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)

- Çalışma zamanında veri önbelleğine program aracılığıyla bir nesne eklemek için, veya sınıfları gibi `StartCaching` bir konak öğesinin `ThisDocument` yöntemini `ThisWorkbook` kullanın. Daha fazla bilgi için [bkz. Nasıl kullanılır: Veri kaynağını](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)program aracılığıyla bir veri Office önbelleğe alın.

  Veri önbelleğine bir nesnesi ekledikten sonra, Word'i başlatmadan veya önbelleğe alınmış verilere erişmeden Excel. Daha fazla bilgi için [bkz. sunucusundaki belgelerde verilere erişme.](../vsto/accessing-data-in-documents-on-the-server.md)

## <a name="requirements-for-data-objects-to-be-cached"></a>Veri nesnelerinin önbelleğe alınma gereksinimleri
 Çözümünüzde bir veri nesnesini önbelleğe alan nesnenin şu gereksinimleri karşılaması gerekir:

- Veya sınıfları gibi bir konak öğesinin okuma/yazma ortak alanı veya `ThisDocument` özelliği `ThisWorkbook` olabilir.

- Dizin oluşturma veya diğer parametreli özellik değildir.

  Buna ek olarak, veri nesnesinin sınıfı tarafından seri hale getirilebilir olması gerekir, yani <xref:System.Xml.Serialization.XmlSerializer> nesne türünün şu özelliklere sahip olması gerekir:

- Genel tür olarak.

- Parametresiz bir ortak oluşturucuya sahip olmalıdır.

- Ek güvenlik ayrıcalıkları gerektiren kodu yürütmez.

- Yalnızca okuma/yazma ortak özelliklerini açığa çıkarma (diğer özellikler yoksayılır).

- Çok boyutlu dizileri açığa çıkarma (iç içe diziler kabul edilir).

- Özelliklerden ve alanlardan arabirimler dönmez.

- Bir koleksiyon <xref:System.Collections.IDictionary> ise uygulanmaz.

  Bir veri nesnesini önbelleğe alır, nesneyi belgede özel bir XML bölümünde depolanan bir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] *XML dizesine* seri hale getirme. Daha fazla bilgi için bkz. [Özel XML bölümlerine genel bakış.](../vsto/custom-xml-parts-overview.md)

## <a name="cached-data-size-limits"></a>Önbelleğe alınmış veri boyutu sınırları
 Bir belgede veri önbelleğine ekleyebilirsiniz toplam veri miktarı ve veri önbelleğinde tek tek herhangi bir nesnenin boyutu için bazı sınırlar vardır. Bu sınırları aşarsanız, veriler veri önbelleğine kaydedilirken uygulama beklenmedik şekilde kapanıyor olabilir.

 Bu sınırları önlemek için şu yönergeleri izleyin:

- Veri önbelleğine 10 MB'den büyük hiçbir nesne ekleme.

- Tek bir belgede veri önbelleğine toplam 100 MB'den fazla veri eklemeyebilirsiniz.

  Bunlar yaklaşık değerlerdir. Tam sınırlar, kullanılabilir RAM ve çalışan işlem sayısı gibi çeşitli faktörlere bağlıdır.

## <a name="control-the-behavior-of-cached-objects"></a>Önbelleğe alınan nesnelerin davranışını denetleme
 Önbelleğe alınmış bir nesnenin davranışı üzerinde daha fazla denetim elde etmek için, önbelleğe <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> alınan nesnenin türüne arabirimini uygulayabilirsiniz. Örneğin, nesne değiştirilse kullanıcıya nasıl bildirildiğini kontrol etmek için bu arabirimi gerçekleştirebilirsiniz. 'nin nasıl uygulandığını gösteren kod örnekleri için, geliştirme örnekleri ve kılavuzlarında Excel Ve Word Dinamik Denetimleri <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> `ControlCollection` Örneği Office [sınıfına bakın.](../vsto/office-development-samples-and-walkthroughs.md)

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Parola korumalı belgelerde önbelleğe alınan verilerde yapılan değişiklikleri kalıcı olarak koruma
 Parola ile korunan bir belgedeki veri nesnelerini önbelleğe asanız, önbelleğe alınan verilerde yapılan değişiklikler kaydedlanmaz. İki yöntemi geçersiz karak önbelleğe alınan verilerde yapılan değişiklikleri kaydedebilirsiniz. Belge kaydedilirken korumayı geçici olarak kaldırmak için bu yöntemleri geçersiz kılın ve kaydetme işlemi tamamlandıktan sonra korumayı yeniden kullanın.

 Daha fazla bilgi için [bkz. Nasıl kullanılır: Parola korumalı bir belgede verileri önbelleğe ekleme.](../vsto/how-to-cache-data-in-a-password-protected-document.md)

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Veri önbelleğine null değerler eklerken veri kaybını önleme
 Veri önbelleğine nesne eklerken, belge kaydedi ve kapatmadan önce önbelleğe alınan tüm nesnelerin **null** olmayan bir değere başlatılması gerekir. Belge kaydedilir ve kapatılırken önbelleğe alınmış herhangi bir nesne **null** değere sahipse, önbelleğe alınan tüm nesneleri veri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] önbelleğinden otomatik olarak kaldırır.

 Tasarım zamanında özniteliğini kullanarak veri önbelleğine **null** değere sahip bir nesne eklersiniz, önbelleğe alınan veri nesnelerini belge açık olmadan önce başlatmak için <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfını kullanabilirsiniz. Belge son kullanıcı tarafından başlatılmadan önce Word veya Excel yüklü olmayan bir sunucuda önbelleğe alınmış verileri başlatmak için bu yararlı olur. Daha fazla bilgi için [bkz. sunucusundaki belgelerde verilere erişme.](../vsto/accessing-data-in-documents-on-the-server.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Verileri çevrimdışı veya sunucuda kullanmak üzere önbelleğe alın](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Nasıl kullanılır: Bir veri kaynağını program aracılığıyla bir Office önbelleğe ekleme](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Nasıl kullanılır: Parola korumalı bir belgede verileri önbelleğe ekleme](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Adım adım kılavuz: Önbelleğe alınmış bir veri kümesi kullanarak ana ayrıntı ilişkisi oluşturma](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
