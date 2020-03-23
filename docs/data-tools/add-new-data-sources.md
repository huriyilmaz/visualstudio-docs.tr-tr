---
title: Yeni veri kaynağı ekleme
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 555d32eb295e944060d2efe0b843e9d157b7c675
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302254"
---
# <a name="add-new-data-sources"></a>Yeni veri kaynağı ekleme

Visual Studio'daki .NET veri araçları bağlamında, *veri kaynağı* terimi bir veri deposuna bağlanan ve verileri bir .NET uygulamasına kullanılabilir hale getiren .NET nesnelerini ifade eder. Visual Studio tasarımcıları, **Veri Kaynakları** penceresinden veritabanı nesnelerini sürükleyip bıraktığınızda verileri formlara bağlayan ortak kodu oluşturmak için veri kaynağının çıktısını tüketebilir. Bu tür bir veri kaynağı şu olabilir:

- Bir tür veritabanıyla ilişkili varlık çerçevesi modelindeki bir sınıf.

- Bir tür veritabanıyla ilişkili bir veri kümesi.

- Windows Communication Foundation (WCF) veri hizmeti veya REST hizmeti gibi bir ağ hizmetini temsil eden sınıf.

- SharePoint hizmetini temsil eden bir sınıf.

- Çözümünüzde bir sınıf veya koleksiyon.

> [!NOTE]
> Veri bağlama özellikleri, veri kümeleri, Entity Framework, LINQ to SQL, WCF veya SharePoint kullanmıyorsanız, "veri kaynağı" kavramı geçerli değildir. SQLCommand nesnelerini kullanarak doğrudan veritabanına bağlanın ve veritabanıyla doğrudan iletişim kurun.

Windows Forms veya Windows Presentation Foundation uygulamasında **Veri Kaynağı Yapılandırma Sihirbazı'nı** kullanarak veri kaynakları oluşturur ve düzenlemezsiniz. Varlık Çerçevesi için önce varlık sınıflarınızı oluşturun ve ardından **Project** > **Add New Data Source'u** (bu makalede daha ayrıntılı olarak açıklanan) seçerek sihirbazı başlatın.

![Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Veri Kaynakları penceresi

Bir veri kaynağı oluşturduktan sonra, **Veri Kaynakları** araç penceresinde görünür.

> [!TIP]
> **Veri Kaynakları** penceresini açmak için projenizin açık olduğundan emin olun ve ardından **Shift**+**Alt**+**D** tuşuna basın veya Diğer**Windows** > Veri**Kaynaklarını** **Görüntüle'yi** > seçin.

**Veri Kaynakları** penceresinden bir veri kaynağını form tasarım yüzeyine veya denetimine sürükleyebilirsiniz. Bu, veri deposundaki verileri görüntüleyen ortak kod oluşturulmasına neden olur.

Aşağıdaki resimde, Windows formuna bırakılan bir veri kümesi gösterilmektedir. Uygulamada **F5'i** seçerseniz, temel veritabanındaki veriler formun denetimlerinde görünür.

![Veri Kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Veritabanı veya veritabanı dosyası için veri kaynağı

Veritabanı veya veritabanı dosyası için veri kaynağı olarak kullanmak üzere bir veri kümesi veya Varlık Çerçevesi modeli oluşturabilirsiniz.

### <a name="dataset"></a>Veri kümesi

Veri kaynağı olarak bir veri kümesi oluşturmak için **Project** > **Add New Data Source'u**seçerek Veri Kaynağı Yapılandırma **Sihirbazı'nı** çalıştırın. **Veritabanı** veri kaynağı türünü seçin ve yeni veya varolan bir veritabanı bağlantısı veya bir veritabanı dosyası belirtmek için istemleri izleyin.

### <a name="entity-classes"></a>Varlık sınıfları

Veri kaynağı olarak varlık çerçevesi modeli oluşturmak için:

1. Varlık sınıflarını oluşturmak için **Varlık Veri Modeli Sihirbazı'nı** çalıştırın. **Proje** > Seç Yeni Öğe > ADO.NET**Varlık Veri Modeli****ekle.**

   ![Yeni Varlık Çerçevesi modeli proje öğesi](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Modeli oluşturmak istediğiniz yöntemi seçin.

   ![Varlık Veri Modeli Sihirbazı](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Modeli veri kaynağı olarak ekleyin. **Nesneler** kategorisini seçtiğinizde oluşturulan sınıflar **Veri Kaynağı Yapılandırma Sihirbazı'nda** görünür.

   ![Varlık Sınıfları ile Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Bir hizmet için veri kaynağı

Bir hizmetten veri kaynağı oluşturmak için **Veri Kaynağı Yapılandırma Sihirbazı'nı** çalıştırın ve **Hizmet** veri kaynağı türünü seçin. Bu, **Solution Explorer'da** projeyi sağ tıklatarak ve **hizmet başvurusu ekle'yi**seçerek de erişebileceğiniz Hizmet **Başvurusu Ekle** iletişim kutusuna açılan kısayol.

Bir hizmetten bir veri kaynağı oluşturduğunuzda, Visual Studio projenize bir hizmet başvurusu ekler. Visual Studio ayrıca, hizmetin döndürdettiği nesnelere karşılık gelen proxy nesneleri de oluşturur. Örneğin, veri kümesini döndüren bir hizmet projenizde veri kümesi olarak temsil edilir; belirli bir türü döndüren bir hizmet, projenizde döndürülen tür olarak temsil edilir.

Aşağıdaki hizmet türlerinden bir veri kaynağı oluşturabilirsiniz:

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Web Hizmetleri

    > [!NOTE]
    > **Veri Kaynakları** penceresinde görünen öğeler, hizmetin döndürdettiği verilere bağlıdır. Bazı **hizmetler, Veri Kaynağı Yapılandırma Sihirbazı'nın** bağlanabilir nesneler oluşturması için yeterli bilgi sağlamayabilir. Örneğin, hizmet yazılmamış bir veri kümesi döndürürse, sihirbazı tamamladığınızda **Veri Kaynakları** penceresinde hiçbir öğe görünmez. Bunun nedeni, yazılmamış veri kümelerinin şema sağlamaması ve bu nedenle sihirbazın veri kaynağını oluşturmak için yeterli bilgiye sahip olmamasıdır.

## <a name="data-source-for-an-object"></a>Bir nesne için veri kaynağı

**Veri Kaynağı Yapılandırma Sihirbazı'nı** çalıştırıp nesne **veri** kaynağı türünü seçerek bir veya daha fazla ortak özelliği ortaya çıkaran herhangi bir nesneden bir veri kaynağı oluşturabilirsiniz. Bir nesnenin tüm ortak özellikleri **Veri Kaynakları** penceresinde görüntülenir. Varlık Çerçevesi kullanıyorsanız ve bir model oluşturduysanız, uygulamanızın veri kaynakları olan varlık sınıflarını burada bulabilirsiniz.

Veri **Nesnelerini Seç** sayfasında, bağlamak istediğiniz nesneleri bulmak için ağaç görünümündeki düğümleri genişletin. Ağaç görünümü, projeniz ve projeniz tarafından başvurulan derlemeler ve diğer projeler için düğümler içerir.

Ağaç görünümünde görünmeyen bir derleme veya projedeki bir nesneye bağlamak istiyorsanız, **Başvuru Ekle'yi** tıklatın ve derlemeye veya projeye başvuruda bulunan başvuru **kutusunu** kullanın. Başvuruyu ekledikten sonra, derleme veya proje ağaç görünümüne eklenir.

> [!NOTE]
> Nesneler ağaç görünümünde görünmeden önce nesnelerinizi içeren projeyi oluşturmanız gerekebilir.

> [!NOTE]
> Sürükle ve bırak veri bağlamayı desteklemek için, arabirimi <xref:System.ComponentModel.ITypedList> veya <xref:System.ComponentModel.IListSource> arabirimi uygulayan nesnelerin varsayılan bir oluşturucuya sahip olması gerekir. Aksi takdirde, Visual Studio veri kaynağı nesnesini anında algılayamaz ve öğeyi tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint listesi için veri kaynağı

Veri Kaynağı Yapılandırma Sihirbazı'nı çalıştırarak **Data Source Configuration Wizard** ve **SharePoint** veri kaynağı türünü seçerek SharePoint listesinden bir veri kaynağı oluşturabilirsiniz. SharePoint, WCF Veri Hizmetleri aracılığıyla verileri açığa çıkarır, bu nedenle SharePoint veri kaynağı oluşturmak bir hizmetten veri kaynağı oluşturmakla aynıdır. **Veri Kaynağı Yapılandırma Sihirbazı'ndaki** **SharePoint** öğesini seçmek, SharePoint sunucusunu işaret ederek SharePoint veri hizmetine bağlandığınız **Hizmet Başvurusu Ekle** iletişim kutusunu açar. Bunun için SharePoint SDK'ya bilgi verilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
