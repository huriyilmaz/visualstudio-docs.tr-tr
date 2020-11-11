---
title: Yeni veri kaynağı ekleme
description: Visual Studio 'da yeni veri kaynakları ekleyin. Veri kaynağı, bir veri deposuna bağlanan ve verileri bir .NET uygulaması için kullanılabilir hale kılan bir .NET nesnesidir.
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ec58528bfe5e1687c4b4edc7f86451c08b04652c
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518680"
---
# <a name="add-new-data-sources"></a>Yeni veri kaynağı ekleme

:::moniker range="vs-2019"
> [!NOTE]
> Bu makalede açıklanan özellikler, .NET Framework Windows Forms ve WPF geliştirmesi için geçerlidir. Visual Studio 2019 ' de (ve önceki sürümlerde), Özellikler .NET Core geliştirmesi için hem WPF hem de Windows Forms için desteklenmez.
:::moniker-end

Visual Studio 'daki .NET veri araçları bağlamında *veri kaynağı* terimi, bir veri deposuna bağlanan ve verileri bir .NET uygulaması için kullanılabilir hale getirmek üzere .NET nesneleri anlamına gelir. Visual Studio tasarımcıları, veri **kaynakları** penceresinden veritabanı nesnelerini sürükleyip bıraktığınızda verileri formlara bağlayan ortak kodu oluşturmak için veri kaynağının çıktısını kullanabilir. Bu tür bir veri kaynağı şu olabilir:

- Bir Entity Framework modelinde, bir veritabanı türüyle ilişkili bir sınıf.

- Bir veritabanı türüyle ilişkili bir veri kümesi.

- Windows Communication Foundation (WCF) veri hizmeti veya REST hizmeti gibi bir ağ hizmetini temsil eden bir sınıf.

- Bir SharePoint hizmetini temsil eden sınıf.

- Çözümünüzde bir sınıf veya koleksiyon.

> [!NOTE]
> Veri bağlama özellikleri, veri kümeleri, Entity Framework, LINQ to SQL, WCF veya SharePoint kullanmıyorsanız, "veri kaynağı" kavramı uygulanmaz. Yalnızca SQLCommand nesnelerini kullanarak doğrudan veritabanına bağlanın ve veritabanıyla doğrudan iletişim kurun.

Veri kaynaklarını bir Windows Forms veya Windows Presentation Foundation uygulamasında **veri kaynağı Yapılandırma Sihirbazı** ' nı kullanarak oluşturur ve düzenleyebilirsiniz. Entity Framework için öncelikle varlık sınıflarınızı oluşturun ve ardından **Proje**  >  **Yeni veri kaynağı Ekle** ' yi seçerek Sihirbazı başlatın (Bu makalenin ilerleyen bölümlerinde daha ayrıntılı açıklanmıştır).

![Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Veri Kaynakları penceresi

Bir veri kaynağı oluşturduktan sonra **veri kaynakları** araç penceresinde görünür.

> [!TIP]
> **Veri kaynakları** penceresini açmak için projenizin açık olduğundan emin olun ve ardından **SHIFT** + **alt** + **D** ' ye basın veya **View**  >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçin.

Veri **kaynakları** penceresinden bir veri kaynağını form tasarım yüzeyine veya denetimine sürükleyebilirsiniz. Bu, veri deposundaki verileri görüntüleyen ortak kodların oluşturulmasına neden olur.

Aşağıdaki çizimde bir Windows formuna bırakılan bir veri kümesi gösterilmektedir. Uygulamada **F5** ' i seçerseniz, temel alınan veritabanındaki veriler formun denetimlerinde görünür.

![Veri kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Veritabanı veya veritabanı dosyası için veri kaynağı

Veritabanı veya veritabanı dosyası için veri kaynağı olarak kullanmak üzere bir veri kümesi veya Entity Framework modeli oluşturabilirsiniz.

### <a name="dataset"></a>Veri kümesi

Veri kaynağı olarak bir veri kümesi oluşturmak için, **Proje** yeni veri kaynağı Ekle ' yi seçerek **veri kaynağı Yapılandırma Sihirbazı** 'nı çalıştırın  >  **Add New Data Source**. **Veritabanı** veri kaynağı türünü seçin ve yeni veya mevcut bir veritabanı bağlantısı ya da bir veritabanı dosyası belirtmek için istemleri izleyin.

### <a name="entity-classes"></a>Varlık sınıfları

Veri kaynağı olarak bir Entity Framework modeli oluşturmak için:

1. Varlık sınıflarını oluşturmak için **varlık veri modeli Sihirbazı 'nı** çalıştırın. **Project**  >  **Add New Item**  >  **ADO.net varlık veri modeli** seçin.

   ![Yeni Entity Framework modeli proje öğesi](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Modeli oluşturmak istediğiniz yöntemi seçin.

   ![Varlık Veri Modeli Sihirbazı](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Modeli bir veri kaynağı olarak ekleyin. Oluşturulan sınıflar, **nesneler** kategorisini seçtiğinizde **veri kaynağı Yapılandırma Sihirbazı** 'nda görüntülenir.

   ![Varlık sınıflarıyla veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Bir hizmet için veri kaynağı

Bir hizmetten veri kaynağı oluşturmak için, **veri kaynağı Yapılandırma Sihirbazı** 'nı çalıştırın ve **hizmet** veri kaynağı türünü seçin. Bu yalnızca **hizmet başvurusu Ekle** iletişim kutusunun bir kısayoludur. bu, **Çözüm Gezgini** projeye sağ tıklayıp **hizmet başvurusu Ekle** ' yi seçerek de erişebilirsiniz.

Bir hizmetten veri kaynağı oluşturduğunuzda, Visual Studio projenize bir hizmet başvurusu ekler. Visual Studio Ayrıca hizmetin döndürdüğü nesnelere karşılık gelen proxy nesnelerini de oluşturur. Örneğin, bir veri kümesi döndüren bir hizmet projenizde veri kümesi olarak temsil edilir; belirli bir türü döndüren bir hizmet, projenizde döndürülen tür olarak temsil edilir.

Aşağıdaki hizmet türlerinden bir veri kaynağı oluşturabilirsiniz:

- [WCF Veri Hizmetleri](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Web hizmetleri

    > [!NOTE]
    > **Veri kaynakları** penceresinde görünen öğeler, hizmetin döndürdüğü verilere bağımlıdır. Bazı hizmetler, **veri kaynağı Yapılandırma Sihirbazı** için bağlanabilir nesneler oluşturmak için yeterli bilgi sağlamayabilir. Örneğin, hizmet türsüz bir veri kümesi döndürürse, Sihirbazı tamamladığınızda **veri kaynakları** penceresinde hiçbir öğe görünmez. Bunun nedeni, türsüz veri kümelerinin bir şema sağlamamasını ve bu nedenle Sihirbazın veri kaynağını oluşturmak için yeterli bilgilere sahip olmamasından kaynaklanır.

## <a name="data-source-for-an-object"></a>Bir nesne için veri kaynağı

**Veri kaynağı Yapılandırma Sihirbazı 'nı** çalıştırarak ve ardından **nesne** veri kaynağı türünü seçerek bir veya daha fazla ortak özellik sunan herhangi bir nesneden veri kaynağı oluşturabilirsiniz. Bir nesnenin tüm ortak özellikleri **veri kaynakları** penceresinde görüntülenir. Entity Framework kullanıyorsanız ve bir model oluşturduysanız, uygulamanız için veri kaynakları olan varlık sınıflarını burada bulabilirsiniz.

**Veri nesnelerini seçin** sayfasında, bağlamak istediğiniz nesneleri bulmak için ağaç görünümündeki düğümleri genişletin. Ağaç görünümü, projeniz için ve projeniz tarafından başvurulan derlemeler ve diğer projeler için düğümler içerir.

Ağaç görünümünde görünmeyen bir derlemede veya projede bir nesneye bağlamak istiyorsanız, **Başvuru Ekle** ' ye tıklayın ve derleme veya projeye bir başvuru eklemek Için **Başvuru Ekle iletişim kutusunu** kullanın. Başvuruyu ekledikten sonra, derleme veya proje ağaç görünümüne eklenir.

> [!NOTE]
> Nesneler ağaç görünümünde görüntülenmeden önce, nesnelerinizi içeren projeyi oluşturmanız gerekebilir.

> [!NOTE]
> Sürükle ve bırak veri bağlamayı desteklemek için, <xref:System.ComponentModel.ITypedList> veya arabirimini uygulayan nesnelerin <xref:System.ComponentModel.IListSource> varsayılan bir oluşturucusu olmalıdır. Aksi halde, Visual Studio veri kaynağı nesnesini örneklemez ve öğeyi tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint listesi için veri kaynağı

**Veri kaynağı Yapılandırma Sihirbazı** 'nı çalıştırarak ve **SharePoint** veri kaynağı türünü seçerek SharePoint listesinden bir veri kaynağı oluşturabilirsiniz. SharePoint verileri WCF Veri Hizmetleri aracılığıyla kullanıma sunar, bu nedenle bir SharePoint veri kaynağı oluşturmak hizmetten veri kaynağı oluşturma ile aynıdır. **Veri kaynağı Yapılandırma Sihirbazı** 'nda **SharePoint** öğesini seçme, SharePoint sunucusuna işaret ederek sharepoint veri hizmetine bağlandığınız **hizmet başvurusu Ekle** iletişim kutusunu açar. Bu, SharePoint SDK 'sını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
