---
title: Veri Kümeleri Oluşturma ve Yapılandırma
description: Veri kümelerini oluşturma ve yapılandırma Visual Studio. Veri kümesi, bir db'den bellekte veri depolar ve bu veriler üzerinde CRUD işlemlerini destekleyen bir nesne kümesidir.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8ce31c2e5a7e5e5f0441c213bd3f320212de5d3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037063"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Nasıl kullanılır: Veri kümelerini Visual Studio

Veri kümesi, veritabanındaki verileri bellekte depolar ve her zaman veritabanına bağlanmaya gerek kalmadan bu veriler üzerinde oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemlerini etkinleştirmek için değişiklik izleme desteği sağlayan nesneler kümesidir. Veri kümeleri, veri iş uygulamaları üzerinde *basit formlar için* tasarlanmıştır. Yeni uygulamalar için verileri bellekte Entity Framework ve modellemek için yeni uygulamalar kullanmayı göz önünde bulundurabilirsiniz. Veri kümeleriyle çalışmak için veritabanı kavramları hakkında temel bilgilere sahipsiniz.

Veri Kaynağı Yapılandırma Sihirbazı'nı kullanarak Visual Studio tasarım zamanında bir <xref:System.Data.DataSet> **türe sahip sınıf oluşturabilirsiniz.** Program aracılığıyla veri kümeleri oluşturma hakkında bilgi için bkz. [Veri kümesi oluşturma (ADO.NET).](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset)

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Veri Kaynağı Yapılandırma Sihirbazı'nı kullanarak yeni bir veri kümesi oluşturma

1. Projenizi Visual Studio açın ve ardından Project Veri Kaynağı **Ekle'yi**  >   seçarak Veri Kaynağı **Yapılandırma Sihirbazı'nı başlatın.**

2. Bağlanmak istediğiniz veri kaynağı türünü seçin.

     ![Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)

3. Veri kümenizin veri kaynağı olacak veritabanını veya veritabanlarını seçin.

     ![Veri kaynağı bağlantı seçin](../data-tools/media/data-source-choose-a-connection.png)

4. Veri kümesinde temsil etmek istediğiniz veritabanından tabloları (veya tek tek sütunları), saklı yordamları, işlevleri ve görünümleri seçin.

     ![Veritabanı nesnelerini seçme](../data-tools/media/raddata-chose-objects.png)

5. **Finish (Son)** düğmesine tıklayın.

   Veri kümesi, içinde bir düğüm **olarak Çözüm Gezgini.**

   ![Çözüm Gezgini'de DataSet](../data-tools/media/dataset-in-solution-explorer.png)

6. Veri kümesi tasarımcısında açmak **Çözüm Gezgini** veri kümesi **düğümüne tıklayın.** Veri kümesinde yer alan her tablonun `TableAdapter` altta temsil edilen ilişkili bir nesnesi vardır. Tablo bağdaştırıcısı, veri kümesi doldurmak ve isteğe bağlı olarak veritabanına komut göndermek için kullanılır.

   ![DataSet Tasarımcısı](../data-tools/media/dataset-designer.png)

7. Tabloları birbirine bağ eden ilişki çizgileri, veritabanında tanımlandığı gibi tablo ilişkilerini temsil ediyor. Varsayılan olarak, veritabanındaki yabancı anahtar kısıtlamaları yalnızca ilişki olarak temsil edilen güncelleştirme ve silme kuralları yok olarak ayarlanır. Genellikle, istediğiniz şey bu. Ancak, hiyerarşik güncelleştirmelerin davranışını değiştirebilirsiniz **İlişki** iletişim kutusunu açmak için satırlara tıklarsınız. Daha fazla bilgi için [bkz. Veri kümelerini ilişkiler ve](../data-tools/relationships-in-datasets.md) [Hiyerarşik güncelleştirme.](../data-tools/hierarchical-update.md)

     ![Veri Kümesi İlişkisi iletişim kutusu](../data-tools/media/raddata-relation-dialog.png)

8. Özellikler penceresinde özelliklerini görmek için tablodaki bir tabloya, tablo bağdaştırıcısına veya sütun **adına** tıklayın. Bazı değerleri burada değiştirebilirsiniz. Kaynak veritabanını değil veri kümesi üzerinde değişiklik yapılanı unutmayın.

     ![DataSet sütun özellikleri](../data-tools/media/dataset-column-properties.png)

9. Veri kümesine yeni tablolar veya tablo bağdaştırıcıları ekleyebilir veya mevcut tablo bağdaştırıcıları için yeni sorgular ekleyebilir ya da bu öğeleri Araç Kutusu sekmesinden sürükleyerek tablolar arasında yeni ilişkiler **belirtebilirsiniz.** Veri Kümesi Tasarımcısı **odakta olduğunda bu** sekme görüntülenir.

     ![Veri Kümesi Araç Kutusu](../data-tools/media/raddata-dataset-toolbox.png)

Ardından, veri kümesine verilerle nasıl doldurmak istediğiniz belirtebilirsiniz. Bunun için **TableAdapter Yapılandırma Sihirbazı'nı kullanırsınız.** Daha fazla bilgi için [bkz. TableAdapters kullanarak veri kümelerini doldurma.](../data-tools/fill-datasets-by-using-tableadapters.md)

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Mevcut bir veri kümesine veritabanı tablosu veya başka bir nesne ekleme

Bu yordamda, ilk olarak veri kümesi oluşturmak için kullanılan veritabanından bir tablo ekleme işlemi gösterir.

1. DataSet Designer'ı **Çözüm Gezgini** için veri kümesi **düğümüne** tıklayın.

2. Veri **kaynaklarının sol** kenar boşluğunda Veri Kaynakları sekmesine Visual Studio veya **arama kutusuna** veri kaynakları yazın.

3. Veri kümesi düğümüne sağ tıklayın ve Sihirbazı ile **Veri Kaynağını Yapılandır'ı seçin.**

     ![Veri Kaynağı bağlam menüsü](../data-tools/media/data-source-context-menu.png)

4. Hangi ek tabloların, saklı yordamların veya diğer veritabanı nesnelerinin veri kümesine eklen olduğunu belirtmek için sihirbazı kullanın.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Veri kümesine tek başına veri tablosu ekleme

1. veri kümenizi **Veri Kümesi Tasarımcısı.**

2. Bir <xref:System.Data.DataTable> sınıfı Araç Kutusunun **DataSet** **sekmesinden Veri Kümesi Tasarımcısı.** 

3. Veri tablolarınızı tanımlamak için sütunlar ekleyin. Tabloya sağ tıklayın ve Sütun **Ekle'yi**  >  **seçin.** Gerekirse **sütunun** veri türünü ve bir anahtarı ayarlamak için Özellikler penceresini kullanın.

Tek başına tabloları verilerle doldurabilirsiniz. Tek başına tabloların tek `Fill` başına tablolarda mantık uygulaması gerekir. Tek başına veri tablolarını doldurma hakkında bilgi için bkz. [DataAdapter'dan Veri Kümesi Doldurma.](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
