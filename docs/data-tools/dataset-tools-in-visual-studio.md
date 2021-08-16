---
title: Veri kümesi araçları
description: Visual Studio bulunan veri kümesi araçlarını gözden geçirin. Veri kümesi iş akışı, veri kümeleri ve N katmanlı mimari ve veri kümeleri ile XML hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fdb068ad34e2261d99e24b7f836d74c642311949345795d8a2d8e34511bbcd54
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347381"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio'daki veri kümesi araçları

> [!NOTE]
> Veri kümeleri ve ilgili sınıflar, uygulamaların veritabanıyla bağlantısı kesildiğinde uygulamaların bellekteki verilerle çalışmasını sağlayan, ilk 2000 ' den eski .NET teknolojileridir. Bunlar özellikle, kullanıcıların verileri değiştirmesini ve değişiklikleri veritabanına geri kalıcı hale getirebilmesini sağlayan uygulamalar için yararlıdır. Veri kümelerinin çok başarılı bir teknoloji olarak kanıtlanmış olmasına rağmen, yeni .NET uygulamalarının Entity Framework kullanmasını öneririz. Entity Framework, tablo verileriyle nesne modelleri olarak çalışmak için daha doğal bir yol sağlar ve daha basit bir programlama arabirimine sahiptir.

`DataSet`Nesne, aslında bir mini veritabanı olan bellek içi bir nesnedir. `DataTable` `DataColumn` `DataRow` Açık bir bağlantı sürdürmek zorunda kalmadan bir veya daha fazla veritabanından verileri depolayabilmeniz ve değiştirebileceğiniz nesneler içerir. Veri kümesi, verilerinde yapılan değişikliklerle ilgili bilgileri saklar, böylece Güncelleştirmeler izlenebilir ve uygulamanız yeniden bağlandığında veritabanına geri gönderilebilir.

Veri kümeleri ve ilgili sınıflar, <xref:System.Data?displayProperty=fullName> .NET API 'sindeki ad alanında tanımlanmıştır. ADO.NET kullanarak, kodlarda dinamik olarak veri kümeleri oluşturabilir ve değiştirebilirsiniz. bu bölümdeki belgelerde, Visual Studio tasarımcıları kullanılarak veri kümeleriyle nasıl çalışılacağı gösterilmektedir. Tasarımcılar aracılığıyla oluşturulan veri kümeleri, veritabanıyla etkileşime geçmek için **TableAdapter** nesnelerini kullanır. Program aracılığıyla oluşturulan veri kümeleri **DataAdapter** nesnelerini kullanır. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz. [DataAdapter ve DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Uygulamanızın verileri yalnızca bir veritabanından okuması, eklemeleri veya silmeleri için ihtiyacı varsa, `DataReader` verileri genel bir `List` nesneye veya başka bir koleksiyon nesnesine almak için bir nesnesi kullanarak genellikle daha iyi performans elde edebilirsiniz. Verileri görüntülüyorsanız, Kullanıcı arabirimini koleksiyona veri bağlayabilirsiniz.

## <a name="dataset-workflow"></a>Veri kümesi iş akışı

Visual Studio, veri kümeleriyle çalışmayı basitleştirmek için araç sağlar. Temel uçtan uca iş akışı:

- Bir veya daha fazla veri kaynağından yeni bir veri kümesi oluşturmak için [veri kaynakları penceresini](add-new-data-sources.md#data-sources-window) kullanın. Veri kümesini yapılandırmak ve özelliklerini ayarlamak için **veri kümesi Tasarımcısı** kullanın. Örneğin, veri kaynağından hangi tabloların ekleneceğini ve her tablodaki sütunları belirtmeniz gerekir. Veri kümesinin gerektirdiği bellek miktarını korumak için dikkatle ' yi seçin. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Yabancı anahtarların doğru şekilde işlenebilmesi için tablolar arasındaki ilişkileri belirtin. Daha fazla bilgi için bkz. [TableAdapters kullanarak veri kümelerini doldur](../data-tools/fill-datasets-by-using-tableadapters.md).

- Veri kümesini dolduran sorgu veya saklı yordamı ve uygulanacak veritabanı işlemlerini (güncelleştirme, silme, vb.) belirtmek için **TableAdapter Yapılandırma sihirbazını** kullanın. Daha fazla bilgi için şu konulara bakın:

  - [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Veri kümelerinde verileri düzenleme](../data-tools/edit-data-in-datasets.md)

  - [Veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md)

  - [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

- Veri kümesindeki verileri sorgulama ve arama. Daha fazla bilgi için bkz. [sorgu veri kümeleri](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] nesnedeki veriler üzerinde [LINQ (dil Ile tümleşik sorgu)](/dotnet/csharp/linq/) olanağı sunar <xref:System.Data.DataSet> . daha fazla bilgi için bkz. [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Kullanıcı arabirimi denetimlerini veri kümesine veya tek tek sütunlarına bağlamak ve hangi sütunların Kullanıcı tarafından düzenlenebilir olduğunu belirtmek için **veri kaynakları** penceresini kullanın. Daha fazla bilgi için bkz. [Visual Studio denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Veri kümeleri ve N katmanlı mimari

N katmanlı uygulamalardaki veri kümeleri hakkında bilgi için, bkz. [n katmanlı uygulamalarda veri kümeleriyle çalışma](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Veri kümeleri ve XML

Veri kümelerini XML 'e ve öğesinden dönüştürme hakkında daha fazla bilgi için bkz. [XML verilerini bir veri kümesine okuma](../data-tools/read-xml-data-into-a-dataset.md) ve [veri kümesini XML olarak kaydetme](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
