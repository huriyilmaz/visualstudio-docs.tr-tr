---
title: Yeni veri kaynağı ekleme
description: Yeni veri kaynaklarını Visual Studio. Veri kaynağı, bir veri deposuna bağlanan ve verileri bir .NET uygulamasında kullanılabilir hale alan bir .NET nesnesidir.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a0d93a2c80afe7863490f0af5578684d699a5980
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631616"
---
# <a name="add-new-data-sources"></a>Yeni veri kaynağı ekleme

:::moniker range=">=vs-2019"
> [!NOTE]
> Bu makalede açıklanan özellikler, .NET Framework Windows Forms ve WPF geliştirme için geçerlidir. Özellikler hem WPF hem de Windows Forms için .NET Core geliştirmesi için destek Windows değildir.
:::moniker-end

Visual Studio'daki .NET veri araçları bağlamında, veri  kaynağı terimi bir veri deposuna bağlanan ve verileri bir .NET uygulamasına kullanılabilir hale alan .NET nesnelerini ifade eder. Veri Visual Studio, veritabanı nesnelerini Veri Kaynakları penceresinden sürükleyip bırakarak verileri formlara bağlayan ortak kodu oluşturmak için veri kaynağının **çıkışını tüketir.** Bu tür bir veri kaynağı şöyle olabilir:

- Bir veritabanı Entity Framework ilişkili bir model sınıfı.

- Bir tür veritabanıyla ilişkilendirilmiş bir veri kümesi.

- Windows Communication Foundation (WCF) veri hizmeti veya REST hizmeti gibi bir ağ hizmetini temsil eden bir sınıf.

- Bir SharePoint temsil eden sınıf.

- Çözümünüzde bir sınıf veya koleksiyon.

> [!NOTE]
> Veri bağlama özellikleri, veri kümeleri, Entity Framework, LINQ to SQL, WCF veya SharePoint kullanıyorsanız , "veri kaynağı" kavramı geçerli değildir. SQLCommand nesnelerini kullanarak doğrudan veritabanına bağlanmanız ve veritabanıyla doğrudan iletişim kurmanız gerekir.

Windows Forms veya Windows Presentation Foundation uygulamasında  Veri Kaynağı Yapılandırma Sihirbazı'nı kullanarak veri Windows Presentation Foundation oluşturur ve düzenlersiniz. Daha Entity Framework önce varlık sınıflarınızı oluşturun ve ardından Yeni Veri Kaynağı **Ekle**'yi Project seçerek sihirbazı başlatın (bu makalenin devamlarında daha ayrıntılı olarak  >   açıklanmıştır).

![Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Veri Kaynakları penceresi

Bir veri kaynağı oluşturdukta, veri kaynağı Veri **Kaynakları araç penceresinde** görünür.

> [!TIP]
> Veri Kaynakları penceresini **açmak için** projenizin açık olduğundan emin olun ve Shift Alt D tuşuna basın veya Diğer Veri Kaynaklarını +  +    >  **Görüntüle'Windows**  >  **seçin.**

Veri kaynaklarını Veri Kaynakları penceresinden **form tasarım** yüzeyine veya denetimine sürükleyebilirsiniz. Bu, veri deposundaki verileri görüntüleyen ortak kodun üretilebitir.

Aşağıdaki çizimde, bir veri kümesi formuna bırakılan bir Windows gösterilmiştir. Uygulamada **F5'i** seçersiniz, temel alınan veritabanındaki veriler formun denetimlerde görünür.

![Veri Kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Veritabanı veya veritabanı dosyası için veri kaynağı

Veritabanı veya veritabanı dosyası için veri kaynağı Entity Framework veri kümesi veya veri kümesi modeli oluşturabilirsiniz.

### <a name="dataset"></a>Veri kümesi

Veri kaynağı olarak veri kümesi oluşturmak  için Yeni Veri Kaynağı Ekle'yi seçerek **Project**  >  **Yapılandırma Sihirbazı'nı çalıştırın.** Veritabanı **veri** kaynağı türünü seçin ve istemleri takip edin ve yeni veya var olan bir veritabanı bağlantısını ya da bir veritabanı dosyasını belirtin.

### <a name="entity-classes"></a>Varlık sınıfları

Veri kaynağı Entity Framework bir veri modeli oluşturmak için:

1. Varlık **sınıflarını Varlık Veri Modeli sihirbazını** çalıştırın. yeni **Project**  >  **Ekle'yi**  >  **ADO.NET Varlık Veri Modeli.**

   ![Yeni Entity Framework modeli proje öğesi](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Modeli oluşturmak istediğiniz yöntemi seçin.

   ![Varlık Veri Modeli Sihirbazı](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Modeli veri kaynağı olarak ekleyin. Oluşturulan sınıflar, Nesneler **kategorisini seçtiğiniz zaman Veri** Kaynağı Yapılandırma Sihirbazı'nda görünür. 

   ![Varlık Sınıfları ile Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Bir hizmetin veri kaynağı

Bir hizmetten veri kaynağı oluşturmak için Veri Kaynağı **Yapılandırma Sihirbazı'nı çalıştırın** ve **Hizmet** veri kaynağı türünü seçin. Bu, Hizmet Başvurusu Ekle iletişim  kutusunun bir kısayolu; bu kısayola, Çözüm Gezgini'de projeye  sağ tıklar ve Hizmet başvurusu **ekle'yi seçerek de erişebilirsiniz.**

Bir hizmetten veri kaynağı oluştururken, Visual Studio projenize bir hizmet başvurusu ekler. Visual Studio, hizmetin döndürdiği nesnelere karşılık gelen ara sunucu nesneleri de oluşturur. Örneğin, veri kümesi döndüren bir hizmet, projenizin içinde bir veri kümesi olarak temsil edilen bir hizmettir; Belirli bir türü döndüren bir hizmet, projenizin içinde döndürülen tür olarak temsil edilir.

Aşağıdaki hizmet türlerinden bir veri kaynağı oluşturabilirsiniz:

- [WCF Veri Hizmetleri](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Web hizmetleri

    > [!NOTE]
    > Veri Kaynakları penceresinde görünen **öğeler,** hizmetin döndürtt olduğu verilere bağımlıdır. Bazı hizmetler, Veri Kaynağı Yapılandırma Sihirbazı'nın **bağlanabilir nesneler oluşturması** için yeterli bilgi sağlamayabilir. Örneğin, hizmet türlanmamış bir veri kümesi döndürürse, sihirbazı tamamlasanız **Veri** Kaynakları penceresinde hiçbir öğe görünmez. Bunun nedeni, yazlanmamış veri kümelerini bir şema sağlamamış olması ve bu nedenle sihirbazın veri kaynağını oluşturmak için yeterli bilgiye sahip olmasıdır.

## <a name="data-source-for-an-object"></a>Bir nesne için veri kaynağı

Veri Kaynağı Yapılandırma Sihirbazı'nı çalıştırarak ve ardından Nesne veri  kaynağı türünü seçerek bir veya daha fazla genel özelliği açığa çıkaran herhangi bir **nesneden** veri kaynağı oluşturabilirsiniz. Bir nesnenin tüm genel özellikleri Veri Kaynakları **penceresinde** görüntülenir. Uygulamanıza Entity Framework model oluştursanız, uygulamanıza veri kaynakları olan varlık sınıflarını burada bulabilirsiniz.

Veri **Nesnelerini Seçin sayfasında,** bağlamak istediğiniz nesneleri bulmak için ağaç görünümündeki düğümleri genişletin. Ağaç görünümü projeniz ve derlemeler ve projeniz tarafından başvurulan diğer projeler için düğümler içerir.

Ağaç görünümünde görünmeen bir derleme veya projedeki bir nesneye bağlamak için  Başvuru Ekle'ye tıklayın ve Başvuru Ekle İletişim Kutusunu kullanarak derlemeye veya projeye başvuru ekleyin.  Başvuru ekledikten sonra derleme veya proje ağaç görünümüne eklenir.

> [!NOTE]
> Nesneler ağaç görünümünde görünmeden önce nesnelerinizi içeren projeyi derlemeniz gerekir.

> [!NOTE]
> Sürükle ve bırak veri bağlamayı desteklemek için, veya arabirimini <xref:System.ComponentModel.ITypedList> uygulayan nesnelerin <xref:System.ComponentModel.IListSource> varsayılan bir oluşturucusu olması gerekir. Aksi Visual Studio veri kaynağı nesnesinin örneğini oluşturmaz ve öğeyi tasarım yüzeyine sürüklerken bir hata görüntüler.

## <a name="data-source-for-a-sharepoint-list"></a>Bir veri listesi SharePoint kaynağı

Veri Kaynağı Yapılandırma Sihirbazı'nı SharePoint veri kaynağı  türünü seçerek bir veri **SharePoint** oluşturabilirsiniz. SharePoint verileri WCF Veri Hizmetleri, bu nedenle SharePoint kaynağı oluşturmak, hizmetten veri kaynağı oluşturmakla aynıdır. Veri **SharePoint** Sihirbazı'nda Hizmet Başvurusu Ekle  öğesi seçerek SharePoint  veri hizmetine bağlanarak SharePoint iletişim kutusunu açar. Bunun için SharePoint SDK gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
