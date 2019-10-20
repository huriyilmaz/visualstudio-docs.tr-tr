---
title: Veri kümesi araçları
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23e4deba53288383a569f6da6e14d27f723825ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657377"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio'daki veri kümesi araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTUN
> Veri kümeleri ve ilgili sınıflar, uygulamaların veritabanıyla bağlantısı kesildiğinde uygulamaların bellekteki verilerle çalışmasını sağlayan, ilk 2000 ' den eski .NET teknolojileridir. Bunlar özellikle, kullanıcıların verileri değiştirmesini ve değişiklikleri veritabanına geri kalıcı hale getirebilmesini sağlayan uygulamalar için yararlıdır. Veri kümelerinin çok başarılı bir teknoloji olarak kanıtlanmış olmasına rağmen, yeni .NET uygulamalarının Entity Framework kullanmasını öneririz. Entity Framework, tablo verileriyle nesne modelleri olarak çalışmak için daha doğal bir yol sağlar ve daha basit bir programlama arabirimine sahiptir.

 Veri kümesi nesnesi, aslında bir mini veritabanı olan bellek içi bir nesnedir. Açık bir bağlantı sürdürmek zorunda kalmadan bir veya daha fazla veritabanından veri depolayabilmeniz ve değiştiremeyeceğiniz DataTable, DataColumn ve DataRow nesnelerini içerir. Veri kümesi, verilerinde yapılan değişikliklerle ilgili bilgileri saklar, böylece Güncelleştirmeler izlenebilir ve uygulamanız yeniden bağlandığında veritabanına geri gönderilebilir.

 Veri kümeleri ve ilgili sınıflar, .NET Framework sınıf kitaplığındaki System. Data ad alanında tanımlanmıştır. Kodda dinamik olarak veri kümeleri oluşturabilir ve değiştirebilirsiniz. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. ADO.NET. Bu bölümdeki belgelerde, Visual Studio tasarımcıları kullanılarak veri kümeleriyle nasıl çalışılacağı gösterilmektedir. Bilmemiz gereken bir şey: tasarımcılar aracılığıyla yapılan veri kümeleri, veritabanı ile etkileşim kurmak için TableAdapter nesnelerini kullanır, ancak programlı olarak DataAdapter nesneleri kullanır. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz. [DataAdapter ve DataReaders](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

 Uygulamanızın yalnızca bir veritabanından veri okuması ve güncelleştirme, ekleme veya silme işlemleri yapması gerekiyorsa, verileri genel liste nesnesine veya başka bir koleksiyon nesnesine almak için bir DataReader nesnesi kullanarak genellikle daha iyi performans elde edebilirsiniz. Verileri görüntülüyorsanız, Kullanıcı arabirimini koleksiyona veri bağlayabilirsiniz.

## <a name="dataset-workflow"></a>Veri kümesi iş akışı
 Visual Studio, veri kümeleriyle çalışmayı basitleştirecek çok sayıda araç sağlar. Temel uçtan uca iş akışı:

- **Veri kaynağı** penceresini, bir veya daha fazla veri kaynağından yeni bir veri kümesi oluşturmak için kullanın. Veri kümesini yapılandırmak ve özelliklerini ayarlamak için **veri kümesi Tasarımcısı** kullanın. Örneğin, veri kaynağından hangi tabloların ekleneceğini ve her tablodaki sütunları belirtmeniz gerekir. Veri kümesinin gerektirdiği bellek miktarını korumak için dikkatle ' yi seçin. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Yabancı anahtarların doğru şekilde işlenebilmesi için tablolar arasındaki ilişkileri belirtin. Daha fazla bilgi için bkz. [TableAdapters kullanarak veri kümelerini doldur](../data-tools/fill-datasets-by-using-tableadapters.md).

- Veri kümesini dolduran sorgu veya saklı yordamı ve uygulanacak veritabanı işlemlerini (güncelleştirme, silme, vb.) belirtmek için **TableAdapter Yapılandırma sihirbazını** kullanın. Daha fazla bilgi için şu konulara bakın:

  - [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Veri kümelerindeki verileri düzenleme](../data-tools/edit-data-in-datasets.md)

  - [Veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md)

  - [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

- Veri kümesindeki verileri sorgulama ve arama. Daha fazla bilgi için bkz. [sorgu veri kümeleri](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)], bir <xref:System.Data.DataSet> nesnesindeki veriler üzerinde [LINQ (dil Ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) olanağı sunar. Daha fazla bilgi için bkz. [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

- Kullanıcı arabirimi denetimlerini veri kümesine veya tek tek sütunlarına bağlamak ve hangi sütunların Kullanıcı tarafından düzenlenebilir olduğunu belirtmek için **veri kaynakları** penceresini kullanın. Daha fazla bilgi için bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Veri kümeleri ve N katmanlı mimari
 N katmanlı uygulamalardaki veri kümeleri hakkında bilgi için, bkz. [n katmanlı uygulamalarda veri kümeleriyle çalışma](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Veri kümeleri ve XML
 Veri kümelerini XML 'e ve öğesinden dönüştürme hakkında daha fazla bilgi için bkz. [XML verilerini bir veri kümesine okuma](../data-tools/read-xml-data-into-a-dataset.md) ve [veri kümesini XML olarak kaydetme](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
