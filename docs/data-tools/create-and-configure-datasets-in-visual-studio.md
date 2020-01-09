---
title: Veri Kümeleri Oluşturma ve Yapılandırma
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8222b1985ab7f765be9b06fdd6abf7cb1e1cb2dc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586919"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Nasıl yapılır: Visual Studio 'da veri kümeleri oluşturma ve yapılandırma

Veri kümesi, bellekteki bir veritabanından veri depolayan ve değişiklik izlemeyi destekleyen bir nesne kümesidir ve veritabanına her zaman bağlı olmaları gerekmeden bu verilerde oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemlerini etkinleştirir. Veri kümeleri, basit için tasarlanmış *veriler üzerinden formlar* iş uygulamaları. Yeni uygulamalar için bellekteki verileri depolamak ve modellemek için Entity Framework kullanarak göz önünde bulundurun. Veri kümeleriyle çalışmak için veritabanı kavramlarını temel bilgiye sahip olmalıdır.

Tasarım zamanında **veri kaynağı Yapılandırma Sihirbazı 'nı**kullanarak Visual Studio 'da yazılı bir <xref:System.Data.DataSet> sınıfı oluşturabilirsiniz. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz. [veri kümesi oluşturma (ADO.net)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Veri Kaynağı Yapılandırma Sihirbazı'nı kullanarak yeni bir veri kümesi oluşturma

1. Projenizi Visual Studio 'da açın ve ardından **proje** > **Yeni veri kaynağı Ekle** ' yi seçerek **veri kaynağı Yapılandırma Sihirbazı**' nı başlatın.

2. Bağlanacağınız veri kaynağı türünü seçin.

     ![Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)

3. Veri kümeniz için veri kaynağı olacak veritabanını veya veritabanlarını seçin.

     ![Veri kaynağı bir bağlantı seçin](../data-tools/media/data-source-choose-a-connection.png)

4. Tablolar (veya tek tek sütun) depolanan yordamları, işlevleri ve görünümleri kümesinde temsil edilmesini istediğiniz veritabanını seçin.

     ![Veritabanı nesnelerini seçin](../data-tools/media/raddata-chose-objects.png)

5. **Son**'a tıklayın.

   Veri kümesi, **Çözüm Gezgini**bir düğüm olarak görünür.

   ![Çözüm Gezgini veri kümesi](../data-tools/media/dataset-in-solution-explorer.png)

6. Veri kümesi **Tasarımcısı**' nda veri kümesini açmak için **Çözüm Gezgini** ' deki veri kümesi düğümüne tıklayın. Veri kümesindeki her tablo, en altta temsil edilen ilişkili bir `TableAdapter` nesnesine sahiptir. Tablo bağdaştırıcısı DataSet'i doldurmak için ve isteğe bağlı olarak komut veritabanına göndermek için kullanılır.

   ![Veri kümesi Tasarımcısı](../data-tools/media/dataset-designer.png)

7. Tabloları bağlanan ilişkisi satırları tablo ilişkileri veritabanında tanımlanan temsil eder. Varsayılan olarak, bir veritabanındaki yabancı anahtar kısıtlamaları yalnızca bir ilişki güncelleştirme ile temsil edilir ve yok olarak ayarlanmış kuralları silin. Genellikle, istediğiniz olmasıdır. Ancak, hiyerarşik güncelleştirmelerin davranışını değiştirebileceğiniz **ilişki** iletişim kutusunu açmak için çizgilere tıklayabilirsiniz. Daha fazla bilgi için [veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md) ve [hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md).

     ![Veri kümesi Ilişkisi iletişim kutusu](../data-tools/media/raddata-relation-dialog.png)

8. Tablo, tablo bağdaştırıcısı veya bir tablodaki sütun adı özelliklerini görmek için tıklayın **özellikleri** penceresi. Bazı değerler burada değiştirebilirsiniz. Yalnızca veri kümesi, kaynak veritabanı değiştirmekte olduğunuz unutmayın.

     ![Veri kümesi sütun özellikleri](../data-tools/media/dataset-column-properties.png)

9. Veri kümesine yeni tablolar veya tablo bağdaştırıcıları ekleyebilir veya mevcut tablo bağdaştırıcıları için yeni sorgular ekleyebilir ya da bu öğeleri **araç kutusu** sekmesinden sürükleyerek tablolar arasında yeni ilişkiler belirtebilirsiniz. Bu sekme, **veri kümesi Tasarımcısı** odaklanıldığında görüntülenir.

     ![Veri kümesi araç kutusu](../data-tools/media/raddata-dataset-toolbox.png)

Ardından, veri kümesinin verilerle nasıl doldurulacağını belirtmek isteyebilirsiniz. Bunun için kullandığınız **TableAdapter Yapılandırma Sihirbazı'nı**. Daha fazla bilgi için [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Varolan bir veri kümesi için bir veritabanı tablosu veya diğer nesne Ekle

Bu yordamda, ilk veri kümesini oluşturmak için kullanılan aynı veritabanından tablo ekleme gösterilmiştir.

1. **Veri kümesi tasarımcısını** odağa getirmek için **Çözüm Gezgini** veri kümesi düğümüne tıklayın.

2. Visual Studio 'nun sol kenarındaki **veri kaynakları** sekmesine tıklayın veya arama kutusuna **veri kaynakları** yazın.

3. Veri kümesi düğümüne sağ tıklayın ve **veri kaynağını sihirbazla Yapılandır**' ı seçin.

     ![Veri kaynağı bağlam menüsü](../data-tools/media/data-source-context-menu.png)

4. Veri kümesine eklenecek ek tabloları, saklı yordamları veya diğer veritabanı nesnelerini belirtmek için Sihirbazı kullanın.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Tek başına veri tablosu ekleme

1. Kümenizde açın **veri kümesi Tasarımcısı**.

2. Sürükleme bir <xref:System.Data.DataTable> gelen sınıfı **veri kümesi** sekmesinde **araç kutusu** üzerine **veri kümesi Tasarımcısı**.

3. Veri tablosu tanımlamak için sütunları ekleyin. Tabloya sağ tıklayıp > **sütun** **Ekle** ' yi seçin. Sütunun veri türünü ve gerekirse bir anahtarı ayarlamak için **Özellikler** penceresini kullanın.

Tek başına tabloları uygulamak için gereken `Fill` mantığı tek başına tablolar, böylece bunları verilerle doldurabilirsiniz. Tek başına veri tablolarını doldurmak hakkında daha fazla bilgi için bkz: [dataadapter'dan bir DataSet doldurma](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
