---
title: Veri Kümeleri Oluşturma ve Yapılandırma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631198"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Visual Studio’da veri kümeleri oluşturma ve yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri *kümesi* , bellekteki bir veritabanından veri depolayan ve değişiklik izlemeyi destekleyen bir nesne kümesidir ve veritabanına her zaman bağlı olmaları gerekmeden bu verilerde oluşturma, okuma, güncelleştirme ve SILME (CRUD) işlemlerini etkinleştirir. Veri kümeleri, veri iş uygulamaları *üzerinde basit formlar* için tasarlanmıştır. Yeni uygulamalar için, verileri bellekte depolamak ve modellemek üzere Entity Framework kullanmayı düşünün. Veri kümeleriyle çalışmak için, veritabanı kavramlarıyla ilgili temel bilgilere sahip olmanız gerekir.

 Tasarım zamanında **veri kaynağı Yapılandırma Sihirbazı**'Nı kullanarak Visual Studio 'da türü belirlenmiş bir <xref:System.Data.DataSet> sınıfı oluşturursunuz. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz. [veri kümesi oluşturma](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Veri kaynağı Yapılandırma Sihirbazı 'Nı kullanarak yeni bir veri kümesi oluşturma

1. **Proje** menüsünde **Yeni veri kaynağı Ekle** ' ye tıklayarak **veri kaynağı Yapılandırma Sihirbazı**' nı başlatın.

2. Bağlanacağınız veri kaynağı türünü seçin.

     ![Veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png "Veri Kaynağı Yapılandırma Sihirbazı")

3. Veritabanları için veri kümeniz için veri kaynağı olacak veritabanını veya veritabanlarını seçin.

     ![Veri kaynağı bir bağlantı seçin](../data-tools/media/data-source-choose-a-connection.png "Veri kaynağı bir bağlantı seçin")

4. Veri kümesinde temsil etmek istediğiniz veritabanındaki tabloları (veya ayrı sütunları), saklı yordamları, işlevleri ve görünümleri seçin.

     ![Veritabanı nesnelerini seçin](../data-tools/media/raddata-chose-objects.png "radveri nesneleri seçti")

5. **Son**'a tıklayın.

6. Veri kümesi, **Çözüm Gezgini**bir düğüm olarak görünür:

     ![Çözüm Gezgini veri kümesi](../data-tools/media/dataset-in-solution-explorer.png "Çözüm Gezgini veri kümesi")

     Bu düğüme tıklayın ve veri kümesi **veri kümesi tasarımcısında**görünür. Veri kümesindeki her tablonun, en altta temsil edilen ilişkili bir TableAdapter nesnesine sahip olduğunu unutmayın. Tablo bağdaştırıcısı, veri kümesini doldurmak için ve isteğe bağlı olarak veritabanına komut göndermek için kullanılır.

     ![Veri kümesi Tasarımcısı](../data-tools/media/dataset-designer.png "Veri kümesi Tasarımcısı")

7. Tabloları bağlayan ilişki çizgileri, veritabanında tanımlandığı şekilde tablo ilişkilerini temsil eder. Varsayılan olarak, bir veritabanındaki yabancı anahtar kısıtlamaları, Update ve DELETE kuralları None olarak ayarlanmış şekilde yalnızca bir ilişki olarak temsil edilir. Genellikle, bu, istediğiniz şeydir. Ancak, hiyerarşik güncelleştirmelerin davranışını değiştirebileceğiniz **ilişki** iletişim kutusunu açmak için çizgilere tıklayabilirsiniz. Daha fazla bilgi için bkz. [veri kümelerinde](../data-tools/relationships-in-datasets.md) ve [hiyerarşik güncelleştirmedeki](../data-tools/hierarchical-update.md)ilişkiler.

     ![Veri kümesi Ilişkisi iletişim kutusu](../data-tools/media/raddata-relation-dialog.png "radveri Ilişkisi iletişim kutusu")

8. **Özellikler penceresinde özelliklerini** görmek için tablodaki tablo, tablo bağdaştırıcısı veya sütun adı ' na tıklayın. Bazı değerleri burada değiştirebilirsiniz. Kaynak veritabanını değil, veri kümesini değiştiriyorsanız yalnızca unutmayın.

     ![Veri kümesi sütun özellikleri](../data-tools/media/dataset-column-properties.png "Veri kümesi sütun özellikleri")

9. Veri kümesine yeni tablolar veya tablo bağdaştırıcıları ekleyebilir veya mevcut tablo bağdaştırıcıları için yeni sorgular ekleyebilir ya da bu öğeleri **araç kutusu** sekmesinden sürükleyerek tablolar arasında yeni ilişkiler belirtebilirsiniz. Bu sekme, **veri kümesi Tasarımcısı** odaklanıldığında görüntülenir.

     ![Veri kümesi araç kutusu](../data-tools/media/raddata-dataset-toolbox.png "radveri veri kümesi araç kutusu")

10. Daha sonra, büyük olasılıkla veri kümesinin verilerle nasıl doldurulacağını belirtmek isteyeceksiniz. Bu şekilde **TableAdapter Yapılandırma Sihirbazı**'nı kullanırsınız. Daha fazla bilgi için bkz. [TableAdapters kullanarak veri kümelerini doldur](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Mevcut bir veri kümesine veritabanı tablosu veya başka nesne ekleme
 Bu yordam, ilk olarak veri kümesini oluşturmak için kullandığınız veritabanından bir tablonun nasıl ekleneceğini gösterir.

1. Veri kümesi tasarımcısını odağa getirmek için **Çözüm Gezgini** veri kümesi düğümüne tıklayın.

2. Visual Studio 'nun sol kenarındaki **veri kaynakları** sekmesine tıklayın veya **hızlı Başlat**'a `Data Sources` girin.

3. Veri kümesi düğümüne sağ tıklayın ve **veri kaynağını sihirbazla Yapılandır** ' ı seçin.

     ![Veri kaynağı bağlam menüsü](../data-tools/media/data-source-context-menu.png "Veri kaynağı bağlam menüsü")

4. Veri kümesine eklenecek ek tabloları veya saklı yordamları veya diğer veritabanı nesnelerini belirtmek için Sihirbazı kullanın.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Bir veri kümesine tek başına veri tablosu ekleme

1. Veri kümenizi **veri kümesi Tasarımcısı**açın.

2. **Araç kutusunun** **veri kümesi** sekmesinden bir <xref:System.Data.DataTable> sınıfını **veri kümesi Tasarımcısı**üzerine sürükleyin.

3. Veri tablonuzu tanımlamak için sütun ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: DataTable 'A sütun ekleme](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4. Tek başına tabloların, verileri verilerle doldurmanız için tek başına tablolarda `Fill` mantığı uygulaması gerekir. Tek başına veri tablolarını doldurma hakkında daha fazla bilgi için bkz. [DataAdapter nesnesinden veri kümesini doldurma](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
