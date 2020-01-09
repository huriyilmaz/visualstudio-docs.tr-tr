---
title: Veri kümesi araçları
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cb41a4e3e4ed1c0032c579779a18c7df0bc22477
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586724"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio'daki veri kümesi araçları

> [!NOTE]
> Veri kümeleri ve ilgili sınıflar, bellekteki verileri veritabanından uygulamaları değilken çalışmak uygulamaları etkinleştirme erken 2000'li yıllardan eski .NET teknolojiden var. Bunlar, kullanıcıların verileri değiştirme ve veritabanına değişiklikleri kalıcı hale getirmek uygulamalar için özellikle yararlıdır. Veri kümeleri çok başarılı bir teknoloji olacak şekilde kanıtlanmış olsa da, yeni .NET uygulamalarını Entity Framework kullanmanızı öneririz. Entity Framework tablosal verileri nesne modellerini olarak çalışmak için daha doğal bir yol sağlar ve daha basit bir programlama arabirimi vardır.

`DataSet` nesnesi, aslında bir mini veritabanı olan bellek içi bir nesnedir. Açık bir bağlantı sürdürmek zorunda kalmadan bir veya daha fazla veritabanından veri depolayabilmeniz ve değiştirebileceğiniz `DataTable`, `DataColumn`ve `DataRow` nesneleri içerir. Güncelleştirmeleri izlenen ve uygulamanızı bağlandığınızda olur veritabanına geri gönderilen veri kümesi, verilerde yapılan değişiklikleri ilgili bilgileri tutar.

Veri kümeleri ve ilgili sınıflar, .NET API 'sindeki <xref:System.Data?displayProperty=fullName> ad alanında tanımlanmıştır. ADO.NET kullanarak, kodda dinamik olarak veri kümeleri oluşturabilir ve değiştirebilirsiniz. Bu bölümdeki belgelere, Visual Studio tasarımcıları kullanarak veri kümeleriyle çalışan işlemi gösterilmektedir. Tasarımcılar aracılığıyla oluşturulan veri kümeleri, veritabanıyla etkileşime geçmek için **TableAdapter** nesnelerini kullanır. Program aracılığıyla oluşturulan veri kümeleri **DataAdapter** nesnelerini kullanır. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz: [DataAdapters ve DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Uygulamanızın verileri yalnızca bir veritabanından okuması, eklemeleri veya silmeleri için ihtiyacı varsa, verileri genel bir `List` nesnesine veya başka bir koleksiyon nesnesine almak için bir `DataReader` nesnesi kullanarak genellikle daha iyi performans elde edebilirsiniz. Verileri görüntülüyorsa, veri kullanıcı arabirimi koleksiyona bağlama.

## <a name="dataset-workflow"></a>Veri kümesi iş akışı

Visual Studio, veri kümeleriyle çalışmayı basitleştirmek için araç sağlar. Temel uçtan uca iş akışı şöyledir:

- Bir veya daha fazla veri kaynağından yeni bir veri kümesi oluşturmak için [veri kaynakları penceresini](add-new-data-sources.md#data-sources-window) kullanın. Kullanım **veri kümesi Tasarımcısı** veri kümesini yapılandırma ve özelliklerini ayarlayın. Örneğin, dahil etmek için veri kaynağından tablolar ve her bir tablodaki hangi sütunların belirtmeniz gerekir. Veri kümesinin gerektirdiği bellek miktarını korumak için dikkatle ' yi seçin. Daha fazla bilgi için [oluşturun ve veri kümeleri yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Tablolar arasında ilişki, yabancı anahtarlar doğru şekilde işlenir böylece belirtin. Daha fazla bilgi için [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md).

- Veri kümesini dolduran sorgu veya saklı yordamı ve uygulanacak veritabanı işlemlerini (güncelleştirme, silme, vb.) belirtmek için **TableAdapter Yapılandırma sihirbazını** kullanın. Daha fazla bilgi için şu konulara bakın:

  - [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Veri kümelerindeki verileri düzenleme](../data-tools/edit-data-in-datasets.md)

  - [Veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md)

  - [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

- Sorgu ve veri kümesinde arayın. Daha fazla bilgi için [sorgu veri kümeleri](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] sağlar [LINQ (dil ile tümleşik sorgu)](/dotnet/csharp/linq/) verileri üzerinde bir <xref:System.Data.DataSet> nesne. Daha fazla bilgi için [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Kullanım **veri kaynakları** penceresi kullanıcı arabirimi denetimleri, veri kümesi veya tek tek sütunlarını bağlamak için ve hangi sütunların kullanıcı tarafından düzenlenebilir olduğunu belirtmek için. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Veri kümeleri ve N katmanlı mimari

N katmanlı uygulamalarda veri kümeleri hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Veri kümeleri ve XML

Veri kümeleri ve XML dönüştürme hakkında daha fazla bilgi için bkz: [okuma XML veri kümesine](../data-tools/read-xml-data-into-a-dataset.md) ve [bir veri kümesini XML olarak kaydetme](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
