---
title: Veri kümeleri arasında ilişki oluşturma
description: Veri kümelerini kullanarak veri kümeleri arasında ilişki Visual Studio. DataRelation nesnelerini ve kısıtlamalarını anlama. Veri Kümesi Yöneticisi'nde el ile veri ilişkisi oluşturun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 40a964f6b5d21f2e5a601cd81d33fafbdd030189
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052700"
---
# <a name="create-relationships-between-datasets"></a>Veri kümeleri arasında ilişki oluşturma
İlgili veri tablolarını içeren veri kümeleri, tablolar arasındaki üst/alt ilişkiyi temsil etmek ve ilişkili kayıtları <xref:System.Data.DataRelation> diğerlerinden geri dönmek için nesneleri kullanır. Veri Kaynağı Yapılandırma Sihirbazı'nı veya Veri Kümesi Tasarımcısı kullanarak ilgili tabloları veri kümelerine **eklemek,** nesnesini sizin için oluşturur <xref:System.Data.DataRelation> ve yapılandırıyor.

nesnesi <xref:System.Data.DataRelation> iki işlev gerçekleştirir:

- Üzerinde çalışmakta olan bir kayıtla ilgili kayıtları kullanılabilir hale olabilir. Bir üst kayıtta ( ) ve bir alt kayıtla ( ) çalışıyorsanız üst kayıtta yer <xref:System.Data.DataRow.GetChildRows%2A> <xref:System.Data.DataRow.GetParentRow%2A> alır.

- Bir üst kaydı silebilirsiniz ilgili alt kayıtları silme gibi bilgi tutarlılığı kısıtlamaları zorlar.

Gerçek birleşim ile bir nesnenin işlevi arasındaki farkı anlamak <xref:System.Data.DataRelation> önemlidir. Gerçek bir birleşimde kayıtlar üst ve alt tablolardan alınır ve tek, düz bir kayıt kümesine alınır. Bir nesnesi <xref:System.Data.DataRelation> kullanırken yeni kayıt kümesi oluşturulmaz. Bunun yerine DataRelation, tablolar arasındaki ilişkiyi izler ve üst ve alt kayıtları eşitler.

## <a name="datarelation-objects-and-constraints"></a>DataRelation nesneleri ve kısıtlamaları
<xref:System.Data.DataRelation>Nesnesi ayrıca aşağıdaki kısıtlamaları oluşturmak ve zorlamak için de kullanılır:

- Tablodaki bir sütunda yinelenen öğe olmadığını garanti altına alan benzersiz bir kısıtlama.

- Bir veri kümesinde üst ve alt tablo arasında bilgi tutarlılığını korumak için kullanılabilir yabancı anahtar kısıtlaması.

Bir nesnede belirttiğiniz <xref:System.Data.DataRelation> kısıtlamalar, uygun nesneleri otomatik olarak oluşturarak veya özellikleri ayararak uygulanır. nesnesini kullanarak bir yabancı anahtar kısıtlaması <xref:System.Data.DataRelation> oluşturursanız, <xref:System.Data.ForeignKeyConstraint> sınıfın örnekleri nesnenin <xref:System.Data.DataRelation> özelliğine <xref:System.Data.DataRelation.ChildKeyConstraint%2A> eklenir.

Benzersiz bir kısıtlama, yalnızca bir veri sütununu özelliği olarak ayararak veya sınıfının bir örneğini nesnenin <xref:System.Data.DataColumn.Unique%2A> `true` <xref:System.Data.UniqueConstraint> <xref:System.Data.DataRelation> özelliğine ekleyerek <xref:System.Data.DataRelation.ParentKeyConstraint%2A> uygulanır. Bir veri kümesinde kısıtlamaları askıya alma hakkında bilgi için [bkz. Veri kümesi doldururken kısıtlamaları kapatma.](../data-tools/turn-off-constraints-while-filling-a-dataset.md)

### <a name="referential-integrity-rules"></a>Bilgi tutarlılığı kuralları
Yabancı anahtar kısıtlaması kapsamında, üç nokta için uygulanan bilgi tutarlılığı kuralları belirtesiniz:

- Üst kayıt güncelleştirildiğinde

- Üst kayıt silindiğinde

- Bir değişiklik kabul edilir veya reddedilirse

Liste listesinde belirtilebilir <xref:System.Data.Rule> ve aşağıdaki tabloda listelenmiştir.

|Yabancı anahtar kısıtlama kuralı|Eylem|
| - |------------|
|<xref:System.Data.Rule.Cascade>|Üst kayıtta yapılan değişiklik (güncelleştirme veya silme), alt tablodaki ilgili kayıtlarda da yapılır.|
|<xref:System.Data.Rule.SetNull>|Alt kayıtlar silinmez, ancak alt kayıtlarda yabancı anahtar olarak <xref:System.DBNull> ayarlanır. Bu ayarla, alt kayıtlar "yalnızlar" olarak bırakabilirsiniz; başka bir şekilde üst kayıtlarla hiçbir ilişkisi yoktur. **Not:** Bu kuralın kullanımı alt tabloda geçersiz verilere neden olabilir.|
|<xref:System.Data.Rule.SetDefault>|İlgili alt kayıtlarda yabancı anahtar varsayılan değerine ayarlanır (sütunun özelliği tarafından <xref:System.Data.DataColumn.DefaultValue%2A> belirlendi).|
|<xref:System.Data.Rule.None>|İlgili alt kayıtlarda değişiklik olmaz. Bu ayarla, alt kayıtlar geçersiz üst kayıtlara başvurular içerebilir.|

Veri kümesi tablolarında güncelleştirmeler hakkında daha fazla bilgi için [bkz. Verileri veritabanına geri kaydetme.](../data-tools/save-data-back-to-the-database.md)

### <a name="constraint-only-relations"></a>Yalnızca kısıtlama ilişkileri
Bir nesnesi oluşturursanız, ilişkinin yalnızca kısıtlamaları zorlamak için kullanıla olacağını belirtme seçeneğiniz vardır; diğer bir ifade, ilgili kayıtlara erişmek için <xref:System.Data.DataRelation> de kullanılmaz. Bu seçeneği, biraz daha verimli ve ilgili kayıtlar özelliğine sahip birden az yöntem içeren bir veri kümesi oluşturmak için kullanabilirsiniz. Ancak, ilgili kayıtlara erişesiniz. Örneğin, yalnızca kısıtlama ilişkisi, hala alt kayıtları olan bir üst kaydı silmenizi sağlar ve üst kayıt üzerinden alt kayıtlara erişemeysiniz.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Veri ilişkisi oluşturmak için veri Veri Kümesi Tasarımcısı
Veri tasarım araçlarını kullanarak veri tabloları oluşturulduğunda Visual Studio, verilerin kaynağından toplanıp toplanamaysa ilişkiler otomatik olarak oluşturulur. Veri tablolarını Araç Kutusunun **DataSet sekmesinden** el ile **eklersiniz,** ilişkiyi el ile oluşturmanız gerekebilir. Program aracılığıyla nesne <xref:System.Data.DataRelation> oluşturma hakkında bilgi için bkz. [DataRelations Ekleme.](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations)

Veri tabloları arasındaki ilişkiler, **ilişkinin bire Veri Kümesi Tasarımcısı** gösteren bir anahtar ve sonsuz glyph ile birlikte veri tablolarında satırlar olarak görünür. Varsayılan olarak, ilişkinin adı tasarım yüzeyinde görünmez.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>İki veri tablosu arasında ilişki oluşturmak için

1. veri kümenizi **Veri Kümesi Tasarımcısı.** Daha fazla bilgi için [bkz. Adım Adım: Veri Kümesi Oluşturma Veri Kümesi Tasarımcısı.](walkthrough-creating-a-dataset-with-the-dataset-designer.md)

2. **DataSet** **araç** kutusundan ilişki nesnesini ilişkide alt veri tablosuna sürükleyin.

     İlişki **iletişim** kutusu açılır ve Alt Tablo kutusu **İlişki** nesnesini üzerine sürüklemiş **tabloyla** birlikte açılır.

3. Üst Tablo kutusundan **üst tabloyu** seçin. Üst tablo, bire çok ilişkisinin "bir" tarafındaki kayıtları içerir.

4. Alt Tablo kutusunda doğru alt tablonun **görüntülendiğinden emin** olun. Alt tablo, bire çok ilişkisinin "çok" tarafında kayıtlar içerir.

5. Ad kutusuna ilişki için bir **ad yazın** veya seçili tablolara göre varsayılan adı bırakın. Bu, kodda gerçek <xref:System.Data.DataRelation> nesnenin adıdır.

6. Anahtar Sütunları ve Yabancı Anahtar Sütunları **listelerinde tabloları** **bir alan sütunları** seçin.

7. İlişki, kısıtlama veya her ikisini birden oluşturma seçeneğini seçin.

8. İç İçe İlişki **kutusunu seçin veya temizleyin.** Bu seçenek seçerek özelliği olarak ayarlar ve bu satırlar XML verileri olarak yazıldığı veya ile eşitlenmiş olduğu zaman ilişkinin alt satırlarının üst sütun içinde iç içe geçmiş <xref:System.Data.DataRelation.Nested%2A> `true` olmasına neden <xref:System.Xml.XmlDataDocument> olur. Daha fazla bilgi için [bkz. DataRelations'i İç İçe Yerleştirme.](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations)

9. Bu tablolarda kayıtlarda değişiklik yaparken uygulanacak kuralları ayarlayın. Daha fazla bilgi için bkz. <xref:System.Data.Rule>.

10. İlişkiyi **oluşturmak** için Tamam'a tıklayın. Tasarımcıda iki tablo arasında bir ilişki çizgisi görünür.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>İlişki adını dosyada görüntülemek Veri Kümesi Tasarımcısı

1. veri kümenizi **Veri Kümesi Tasarımcısı.** Daha fazla bilgi için [bkz. Adım Adım: Veri Kümesi Oluşturma Veri Kümesi Tasarımcısı.](walkthrough-creating-a-dataset-with-the-dataset-designer.md)

2. İlişki adını **görüntülemek** için Veri **menüsünde İlişki Etiketlerini** Göster komutunu seçin. İlişki adını gizlemek için bu komutun temizlen.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md)
