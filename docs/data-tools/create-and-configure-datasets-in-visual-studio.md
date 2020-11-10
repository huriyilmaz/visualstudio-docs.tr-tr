---
title: Veri Kümeleri Oluşturma ve Yapılandırma
description: Visual Studio 'da veri kümeleri oluşturun ve yapılandırın. Veri kümesi, verileri bir DB 'den bellekte depolayan ve bu verilerdeki CRUD işlemlerini destekleyen bir nesne kümesidir.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5a9a10d68b5b0617b5c4e2152cbbbb920a7c683f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435410"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Nasıl yapılır: Visual Studio 'da veri kümeleri oluşturma ve yapılandırma

Veri kümesi, bellekteki bir veritabanından veri depolayan ve değişiklik izlemeyi destekleyen bir nesne kümesidir ve veritabanına her zaman bağlı olmaları gerekmeden bu verilerde oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemlerini etkinleştirir. Veri kümeleri, veri iş uygulamaları *üzerinde basit formlar* için tasarlanmıştır. Yeni uygulamalar için, verileri bellekte depolamak ve modellemek üzere Entity Framework kullanmayı düşünün. Veri kümeleriyle çalışmak için, veritabanı kavramlarıyla ilgili temel bilgilere sahip olmanız gerekir.

<xref:System.Data.DataSet>Tasarım zamanında **veri kaynağı Yapılandırma Sihirbazı** 'Nı kullanarak Visual Studio 'da yazılı bir sınıf oluşturabilirsiniz. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz. [veri kümesi oluşturma (ADO.net)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Veri kaynağı Yapılandırma Sihirbazı 'Nı kullanarak yeni bir veri kümesi oluşturma

1. Projenizi Visual Studio 'da açın ve ardından **Proje**  >  **Yeni veri kaynağı Ekle** ' yi seçerek **veri kaynağı Yapılandırma Sihirbazı 'nı** başlatın.

2. Bağlanacağınız veri kaynağı türünü seçin.

     ![Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)

3. Veri kümeniz için veri kaynağı olacak veritabanını veya veritabanlarını seçin.

     ![Veri kaynağı bir bağlantı seçin](../data-tools/media/data-source-choose-a-connection.png)

4. Veri kümesinde temsil etmek istediğiniz veritabanındaki tabloları (veya ayrı sütunları), saklı yordamları, işlevleri ve görünümleri seçin.

     ![Veritabanı nesnelerini seçin](../data-tools/media/raddata-chose-objects.png)

5. **Finish (Son)** düğmesine tıklayın.

   Veri kümesi, **Çözüm Gezgini** bir düğüm olarak görünür.

   ![Çözüm Gezgini veri kümesi](../data-tools/media/dataset-in-solution-explorer.png)

6. Veri kümesi **Tasarımcısı** ' nda veri kümesini açmak için **Çözüm Gezgini** ' deki veri kümesi düğümüne tıklayın. Veri kümesindeki her tablo `TableAdapter` , en altta temsil edilen ilişkili bir nesne içerir. Tablo bağdaştırıcısı, veri kümesini doldurmak için ve isteğe bağlı olarak veritabanına komut göndermek için kullanılır.

   ![Veri kümesi Tasarımcısı](../data-tools/media/dataset-designer.png)

7. Tabloları bağlayan ilişki çizgileri, veritabanında tanımlandığı şekilde tablo ilişkilerini temsil eder. Varsayılan olarak, bir veritabanındaki yabancı anahtar kısıtlamaları, Update ve DELETE kuralları None olarak ayarlanmış şekilde yalnızca bir ilişki olarak temsil edilir. Genellikle, bu, istediğiniz şeydir. Ancak, hiyerarşik güncelleştirmelerin davranışını değiştirebileceğiniz **ilişki** iletişim kutusunu açmak için çizgilere tıklayabilirsiniz. Daha fazla bilgi için bkz. [veri kümelerinde](../data-tools/relationships-in-datasets.md) ve [hiyerarşik güncelleştirmedeki](../data-tools/hierarchical-update.md)ilişkiler.

     ![Veri kümesi Ilişkisi iletişim kutusu](../data-tools/media/raddata-relation-dialog.png)

8. **Özellikler penceresinde özelliklerini** görmek için tablodaki tablo, tablo bağdaştırıcısı veya sütun adı ' na tıklayın. Bazı değerleri burada değiştirebilirsiniz. Kaynak veritabanını değil, veri kümesini değiştiriyorsanız yalnızca unutmayın.

     ![Veri kümesi sütun özellikleri](../data-tools/media/dataset-column-properties.png)

9. Veri kümesine yeni tablolar veya tablo bağdaştırıcıları ekleyebilir veya mevcut tablo bağdaştırıcıları için yeni sorgular ekleyebilir ya da bu öğeleri **araç kutusu** sekmesinden sürükleyerek tablolar arasında yeni ilişkiler belirtebilirsiniz. Bu sekme, **veri kümesi Tasarımcısı** odaklanıldığında görüntülenir.

     ![Veri kümesi araç kutusu](../data-tools/media/raddata-dataset-toolbox.png)

Ardından, veri kümesinin verilerle nasıl doldurulacağını belirtmek isteyebilirsiniz. Bu şekilde **TableAdapter Yapılandırma Sihirbazı** 'nı kullanırsınız. Daha fazla bilgi için bkz. [TableAdapters kullanarak veri kümelerini doldur](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Mevcut bir veri kümesine veritabanı tablosu veya başka nesne ekleme

Bu yordam, ilk olarak veri kümesini oluşturmak için kullandığınız veritabanından bir tablonun nasıl ekleneceğini gösterir.

1. **Veri kümesi tasarımcısını** odağa getirmek için **Çözüm Gezgini** veri kümesi düğümüne tıklayın.

2. Visual Studio 'nun sol kenarındaki **veri kaynakları** sekmesine tıklayın veya arama kutusuna **veri kaynakları** yazın.

3. Veri kümesi düğümüne sağ tıklayın ve **veri kaynağını sihirbazla Yapılandır** ' ı seçin.

     ![Veri kaynağı bağlam menüsü](../data-tools/media/data-source-context-menu.png)

4. Veri kümesine eklenecek ek tabloları, saklı yordamları veya diğer veritabanı nesnelerini belirtmek için Sihirbazı kullanın.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Bir veri kümesine tek başına veri tablosu ekleme

1. Veri kümenizi **veri kümesi Tasarımcısı** açın.

2. <xref:System.Data.DataTable> **Araç kutusunun** **veri kümesi** sekmesinden bir sınıfı **veri kümesi Tasarımcısı** sürükleyin.

3. Veri tablonuzu tanımlamak için sütun ekleyin. Tabloya sağ tıklayıp sütun **Ekle** ' yi seçin  >  **Column**. Sütunun veri türünü ve gerekirse bir anahtarı ayarlamak için **Özellikler** penceresini kullanın.

Tek başına tabloların, `Fill` verileri verilerle doldurmanız için tek başına tablolarda mantık uygulaması gerekir. Tek başına veri tablolarını doldurma hakkında daha fazla bilgi için bkz. [DataAdapter nesnesinden veri kümesini doldurma](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
