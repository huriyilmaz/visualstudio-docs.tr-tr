---
title: Veri kümesi araçları
description: Visual Studio'da bulunan veri kümesi araçlarını gözden Visual Studio. Veri kümesi iş akışı, veri kümeleri ve N katmanlı mimari, veri kümeleri ve XML hakkında bilgi okuyun.
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
ms.openlocfilehash: 1e021a8ab30829aedd0a695a53993998e312ff81
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631424"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio'daki veri kümesi araçları

> [!NOTE]
> Veri kümeleri ve ilgili sınıflar, 2000'in başlarındaki eski .NET teknolojileridir ve uygulamaların veritabanı bağlantısı kesilirken bellekte verilerle çalışmasına olanak sağlar. Bunlar özellikle kullanıcıların verileri değiştirmesini ve değişiklikleri veritabanına geri kalıcı olarak devam etmesi sağlayan uygulamalar için kullanışlıdır. Veri kümeleri çok başarılı bir teknoloji olsa da, yeni .NET uygulamalarının veri kümelerini Entity Framework. Entity Framework tablosal verilerle nesne modelleri olarak çalışmak için daha doğal bir yol sağlar ve daha basit bir programlama arabirimine sahiptir.

Nesne, `DataSet` temelde mini veritabanı olan bellek içinde bir nesnedir. Açık bir bağlantı sürdürmek zorunda kalmadan bir veya daha fazla veritabanındaki verileri depolandırarak değiştirerek , `DataTable` `DataColumn` ve `DataRow` nesnelerini içerir. Veri kümesi, verilerine yapılan değişikliklerle ilgili bilgileri bulundurarak uygulamanıza yeniden bağlandığınızda güncelleştirmelerin izlenebilir ve veritabanına geri gönderebilirsiniz.

Veri kümeleri ve ilgili sınıflar <xref:System.Data?displayProperty=fullName> .NET API'sinde ad alanı içinde tanımlanır. Veri kümelerini kodda dinamik olarak oluşturmak ve değiştirmek için ADO.NET. Bu bölümdeki belgelerde, veri kümeleriyle veri kümeleriyle çalışma hakkında Visual Studio yer almaktadır. Tasarımcılar aracılığıyla oluşturulan veri kümeleri, veritabanıyla etkileşim **kurmak için TableAdapter** nesnelerini kullanır. Program aracılığıyla oluşturulan veri kümeleri **DataAdapter nesnelerini** kullanır. Program aracılığıyla veri kümeleri oluşturma hakkında bilgi için bkz. [DataAdapters ve DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Uygulamanın yalnızca bir veritabanından veri okuması ve güncelleştirme, ekleme veya silme işlemleri gerçekleştirmesine gerek yoksa, genellikle verileri genel bir nesneye veya başka bir koleksiyon nesnesine almak için bir nesnesi kullanarak daha iyi performans `DataReader` `List` elde edersiniz. Verileri görüntüleniyorsanız kullanıcı arabirimini koleksiyona veri olarak bebilirsiniz.

## <a name="dataset-workflow"></a>Veri kümesi iş akışı

Visual Studio, veri kümeleriyle çalışmayı basitleştirmek için araç sağlar. Temel uz- uç iş akışı şu şekildedir:

- Bir veya [daha fazla veri](add-new-data-sources.md#data-sources-window) kaynağından yeni bir veri kümesi oluşturmak için Veri Kaynakları penceresini kullanın. Veri **Veri Kümesi Tasarımcısı** yapılandırmak ve özelliklerini ayarlamak için kümeyi kullanın. Örneğin, hangi tabloların dahil etmek için veri kaynağından ve her tablodan hangi sütunların belirtmelisiniz. Veri kümesi için gereken bellek miktarını korumak için dikkatli bir şekilde seçin. Daha fazla bilgi için [bkz. Veri kümeleri oluşturma ve yapılandırma.](../data-tools/create-and-configure-datasets-in-visual-studio.md)

- Yabancı anahtarların doğru şekilde işlemesi için tablolar arasındaki ilişkileri belirtin. Daha fazla bilgi için [bkz. TableAdapters kullanarak veri kümelerini doldurma.](../data-tools/fill-datasets-by-using-tableadapters.md)

- **TableAdapter Yapılandırma** Sihirbazı'nı kullanarak veri kümesini ve hangi veritabanı işlemlerinin (güncelleştirme, silme, gibi) uygulandığını belirten sorguyu veya saklı yordamı belirtin. Daha fazla bilgi için şu konulara bakın:

  - [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Veri kümelerini düzenleme](../data-tools/edit-data-in-datasets.md)

  - [Veri kümelerini doğrulama](../data-tools/validate-data-in-datasets.md)

  - [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

- Veri kümesinde verileri sorgulama ve arama. Daha fazla bilgi için [bkz. Veri kümelerini sorgulama.](../data-tools/query-datasets.md) [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] bir [nesnesinde veriler üzerinde LINQ (Dil](/dotnet/csharp/linq/) ile Tümleşik Sorgu) <xref:System.Data.DataSet> sağlar. Daha fazla bilgi için [bkz. LINQ to DataSet.](/dotnet/framework/data/adonet/linq-to-dataset)

- Kullanıcı arabirimi **denetimlerini** veri kümesine veya tek tek sütunlarına bağlamak ve hangi sütunların kullanıcı tarafından düzenlenebilir olduğunu belirtmek için Veri Kaynakları penceresini kullanın. Daha fazla bilgi için [bkz. denetimlerini Visual Studio.](../data-tools/bind-controls-to-data-in-visual-studio.md)

## <a name="datasets-and-n-tier-architecture"></a>Veri kümeleri ve N katmanlı mimari

N katmanlı uygulamalarda veri kümeleri hakkında bilgi için [bkz. N katmanlı uygulamalarda veri kümeleriyle çalışma.](../data-tools/work-with-datasets-in-n-tier-applications.md)

## <a name="datasets-and-xml"></a>Veri kümeleri ve XML

Veri kümelerini XML'ye ve XML'den dönüştürme hakkında bilgi için bkz. [XML](../data-tools/read-xml-data-into-a-dataset.md) verilerini bir veri kümesine okuma ve Veri [kümelerini XML olarak kaydetme.](../data-tools/save-a-dataset-as-xml.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
