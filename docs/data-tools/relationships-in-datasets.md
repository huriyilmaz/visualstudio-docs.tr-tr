---
title: Veri kümeleri arasında ilişki oluşturma
description: Visual Studio 'da veri kümeleri arasında ilişkiler oluşturun. DataRelation nesnelerini ve kısıtlamalarını anlayın. Veri kümesi Yöneticisi 'nde el ile bir veri ilişkisi oluşturun.
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
ms.workload:
- data-storage
ms.openlocfilehash: 92e1a03a9a72b550c77aa734c4a9ff2d0b184839
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866612"
---
# <a name="create-relationships-between-datasets"></a>Veri kümeleri arasında ilişki oluşturma
İlişkili veri tabloları içeren veri kümeleri <xref:System.Data.DataRelation> , tablolar arasında bir üst/alt ilişkiyi temsil etmek ve birbiriyle ilişkili kayıtları döndürmek için nesneleri kullanır. **Veri kaynağı Yapılandırma Sihirbazı**' nı kullanarak veya **veri kümesi tasarımcısı**, ilgili tabloları veri kümelerine eklemek <xref:System.Data.DataRelation> sizin için nesneyi oluşturur ve yapılandırır.

<xref:System.Data.DataRelation>Nesnesi iki işlev gerçekleştirir:

- Bu, üzerinde çalıştığınız bir kayıtla ilgili kayıtları kullanılabilir hale getirir. Bir üst kaydımız ( <xref:System.Data.DataRow.GetChildRows%2A> ) ve bir alt kayıtla çalışıyorsanız bir üst kaydımız () alt kayıt sağlar <xref:System.Data.DataRow.GetParentRow%2A> .

- Bir üst kaydı sildiğinizde ilgili alt kayıtları silme gibi, başvuru bütünlüğü için kısıtlamalar uygulayabilir.

Bir nesnenin doğru JOIN ve işlevi arasındaki farkı anlamak önemlidir <xref:System.Data.DataRelation> . Doğru bir birleşimde, kayıtlar üst ve alt tablolardan alınır ve tek ve düz bir kayıt kümesine konur. Bir <xref:System.Data.DataRelation> nesne kullandığınızda, yeni bir kayıt kümesi oluşturulmaz. Bunun yerine, DataRelation, tablolar arasındaki ilişkiyi izler ve üst ve alt kayıtları eşitlenmiş halde tutar.

## <a name="datarelation-objects-and-constraints"></a>DataRelation nesneleri ve kısıtlamaları
Bir <xref:System.Data.DataRelation> nesne ayrıca aşağıdaki kısıtlamaları oluşturmak ve zorlamak için de kullanılır:

- Tablodaki bir sütunun yinelenen değer içermesiz olmasını garanti eden benzersiz bir kısıtlama.

- Bir veri kümesindeki üst ve alt tablo arasında başvurusal bütünlüğü korumak için kullanılabilen bir yabancı anahtar kısıtlaması.

Bir nesnede belirttiğiniz kısıtlamalar <xref:System.Data.DataRelation> , otomatik olarak uygun nesneleri oluşturarak veya özellikleri ayarlayarak uygulanır. Nesnesini kullanarak bir yabancı anahtar kısıtlaması oluşturursanız <xref:System.Data.DataRelation> , <xref:System.Data.ForeignKeyConstraint> sınıfın örnekleri <xref:System.Data.DataRelation> nesnenin <xref:System.Data.DataRelation.ChildKeyConstraint%2A> özelliğine eklenir.

Benzersiz bir kısıtlama, <xref:System.Data.DataColumn.Unique%2A> bir veri sütununun özelliği, `true` <xref:System.Data.UniqueConstraint> nesnenin özelliğine sınıfının bir örneğini eklenerek ya da olarak ayarlanarak uygulanır <xref:System.Data.DataRelation> <xref:System.Data.DataRelation.ParentKeyConstraint%2A> . Bir veri kümesindeki kısıtlamaları askıya alma hakkında daha fazla bilgi için bkz. [veri kümesini doldururken kısıtlamaları](../data-tools/turn-off-constraints-while-filling-a-dataset.md)kapatma.

### <a name="referential-integrity-rules"></a>Başvurusal bütünlük kuralları
Yabancı anahtar kısıtlamasının bir parçası olarak, üç noktaya uygulanan başvurusal bütünlük kuralları belirtebilirsiniz:

- Bir üst kayıt güncelleştirilirken

- Bir üst kayıt silindiğinde

- Bir değişiklik kabul edildiğinde veya reddedildiğinde

Yapabileceğiniz kurallar <xref:System.Data.Rule> numaralandırmada belirtilir ve aşağıdaki tabloda listelenmiştir.

|Yabancı anahtar kısıtlama kuralı|Eylem|
| - |------------|
|<xref:System.Data.Rule.Cascade>|Üst kayıtta yapılan değişiklik (güncelleştirme veya silme) alt tablodaki ilgili kayıtlarda de yapılır.|
|<xref:System.Data.Rule.SetNull>|Alt kayıtlar silinmez, ancak alt kayıtlardaki yabancı anahtar olarak ayarlanır <xref:System.DBNull> . Bu ayar ile alt kayıtlar "artık" olarak bırakılabilir; diğer bir deyişle, üst kayıtlarla hiçbir ilişkisi yoktur. **Note:** Bu kuralın kullanılması, alt tabloda geçersiz veriler oluşmasına neden olabilir.|
|<xref:System.Data.Rule.SetDefault>|İlişkili alt kayıtlardaki yabancı anahtar varsayılan değerine ayarlanır (sütunun özelliği tarafından belirlenen şekilde <xref:System.Data.DataColumn.DefaultValue%2A> ).|
|<xref:System.Data.Rule.None>|İlgili alt kayıtlarda değişiklik yapılmaz. Bu ayar ile alt kayıtlar, geçersiz üst kayıtlara başvuru içerebilir.|

Veri kümesi tablolarındaki güncelleştirmeler hakkında daha fazla bilgi için bkz. [verileri veritabanına geri kaydetme](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Yalnızca kısıtlama ilişkileri
Bir <xref:System.Data.DataRelation> nesne oluşturduğunuzda, ilişkinin yalnızca kısıtlamaları zorlamak için kullanıldığını belirtme seçeneğiniz vardır. diğer bir deyişle, ilgili kayıtlara erişmek için de kullanılmaz. Bu seçeneği, biraz daha verimli bir veri kümesi oluşturmak ve ilgili kayıtlar özelliğiyle bunlardan daha az metot içermesi için kullanabilirsiniz. Bununla birlikte, ilgili kayıtlara erişemeyeceksiniz. Örneğin, yalnızca kısıtlama ilişkisi, hala alt kayıtları olan bir üst kaydı silmenizi önler ve üst öğe üzerinden alt kayıtlara erişemezsiniz.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Veri Kümesi Tasarımcısı bir veri ilişkisini el ile oluşturma
Visual Studio 'daki veri tasarım araçlarını kullanarak veri tabloları oluşturduğunuzda, bilgiler verilerinizin kaynağından toplanarak ilişkiler otomatik olarak oluşturulur. **Araç kutusunun** veri **kümesi** sekmesinden veri tabloları el ile eklerseniz, ilişkiyi el ile oluşturmanız gerekebilir. Program aracılığıyla nesne oluşturma hakkında bilgi için <xref:System.Data.DataRelation> bkz. [DataRelation 'ı ekleme](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).

Veri tabloları arasındaki ilişkiler, ilişkinin tek-çok yönünü gösteren anahtar ve sonsuz bir karakter içeren **veri kümesi Tasarımcısı** satır olarak görünür. Varsayılan olarak, ilişkinin adı tasarım yüzeyinde görünmez.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>İki veri tablosu arasında bir ilişki oluşturmak için

1. Veri kümenizi **veri kümesi Tasarımcısı** açın. Daha fazla bilgi için bkz. [Izlenecek yol: veri kümesi Tasarımcısı veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. **Veri kümesi** araç kutusundan **ilişki nesnesini,** ilişkideki alt veri tablosuna sürükleyin.

     İlişki **iletişim kutusu** açılarak **alt tablo** kutusunu, **ilişki** nesnesini sürüklediğiniz tabloyla birlikte doldurarak açılır.

3. Üst **tablo** kutusundan üst tabloyu seçin. Üst tablo, bire çok ilişkinin "bir" tarafındaki kayıtları içerir.

4. **Alt tablo** kutusunda doğru alt tablonun görüntülendiğini doğrulayın. Alt tablo, bire çok ilişkinin "çok" tarafındaki kayıtları içerir.

5. **Ad** kutusuna ilişki için bir ad yazın veya seçili tablolara göre varsayılan adı bırakın. Bu, <xref:System.Data.DataRelation> koddaki gerçek nesnenin adıdır.

6. **Anahtar sütunlardaki** ve **yabancı anahtar sütunları** listelerindeki tabloları birleştiren sütunları seçin.

7. Bir ilişki, kısıtlama veya her ikisinin de oluşturulup oluşturulmayacağını seçin.

8. **Iç Içe geçmiş ilişki** kutusunu seçin veya temizleyin. Bu seçeneğin belirlenmesi <xref:System.Data.DataRelation.Nested%2A> özelliğini olarak ayarlar `true` ve bu satırlar XML verisi olarak yazıldığında veya ile eşitlendiğinde ilişkinin alt satırlarının üst sütun içinde iç içe olmasına neden olur <xref:System.Xml.XmlDataDocument> . Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).

9. Bu tablolardaki kayıtlarda değişiklik yaparken uygulanacak kuralları ayarlayın. Daha fazla bilgi için bkz. <xref:System.Data.Rule>.

10. İlişkiyi oluşturmak için **Tamam** ' ı tıklatın. İki tablo arasındaki Tasarımcıda bir ilişki satırı görünür.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Veri Kümesi Tasarımcısı bir ilişki adı görüntüleme

1. Veri kümenizi **veri kümesi Tasarımcısı** açın. Daha fazla bilgi için bkz. [Izlenecek yol: veri kümesi Tasarımcısı veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. **Veri** menüsünde Ilişki **etiketlerini göster** komutunu seçerek ilişki adını görüntüleyin. İlişki adını gizlemek için bu komutu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md)
