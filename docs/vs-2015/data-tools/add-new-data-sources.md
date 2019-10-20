---
title: Yeni veri kaynakları ekle | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85c07ad7995bc614df4b988bb17fa8977452b5d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673058"
---
# <a name="add-new-data-sources"></a>Yeni veri kaynağı ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'daki .NET veri araçları bağlamında *veri kaynağı* terimi, bir veri deposuna bağlanan ve verileri bir .NET uygulamasına sunan .net nesnelerine başvurur. Visual Studio tasarımcıları, veri **kaynakları** penceresinden veritabanı nesnelerini sürükleyip bıraktığınızda verileri formlara bağlayan ortak kodu oluşturmak için veri kaynağının çıktısını kullanabilir. Bu tür bir veri kaynağı şu olabilir:

- Bir Entity Framework modelinde, bir veritabanı türüyle ilişkili bir sınıf.

- Bir veritabanı türüyle ilişkili bir veri kümesi.

- Windows Communication Foundation (WCF) veri hizmeti veya REST hizmeti gibi bir ağ hizmetini temsil eden bir sınıf.

- Bir SharePoint hizmetini temsil eden sınıf.

- Çözümünüzde bir sınıf veya koleksiyon.

> [!NOTE]
> Veri bağlama özellikleri, veri kümeleri, Entity Framework, LINQ to SQL, WCF veya SharePoint kullanmıyorsanız, "veri kaynağı" kavramı uygulanmaz. Yalnızca SQLCommand nesnelerini kullanarak doğrudan veritabanına bağlanın ve veritabanıyla doğrudan iletişim kurun.

 Veri kaynaklarını bir Windows Forms veya Windows Presentation Foundation uygulamasında **veri kaynağı Yapılandırma Sihirbazı** ' nı kullanarak oluşturur ve düzenleyebilirsiniz. Entity Framework için öncelikle varlık sınıflarınızı oluşturun ve ardından **proje**  > **Yeni veri kaynağı Ekle** ' yi seçerek Sihirbazı başlatın (Bu makalenin ilerleyen bölümlerinde daha ayrıntılı açıklanmıştır).

 ![Veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png "Veri Kaynağı Yapılandırma Sihirbazı")

 Veri kaynağı oluşturduktan sonra, **veri kaynakları** araç penceresinde görünür (SHIFT + alt + D veya  > **diğer Windows**  > **veri kaynağını** **görüntüle** ). Veri **kaynakları** penceresinden bir veri kaynağını form tasarım yüzeyine veya denetimine sürükleyebilirsiniz. Bu, ortak kodların oluşturulmasına neden olur — veri deposunda kullanıcıya ait verileri görüntüleyen kod. Aşağıdaki çizimde bir Windows formuna bırakılan bir veri kümesi gösterilmektedir. Uygulamada F5 ' i seçtiyseniz, temel alınan veritabanındaki veriler formun denetimlerinde görünür.

 ![Veri kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png "radveri veri kaynağı sürükleme işlemi")

## <a name="data-source-for-a-database-or-a-database-file"></a>Veritabanı veya veritabanı dosyası için veri kaynağı

### <a name="dataset"></a>Veri kümesi
 Veri kaynağı olarak bir veri kümesi oluşturmak için **veri kaynağı Yapılandırma Sihirbazı** 'nı çalıştırın (**Proje**  > **Yeni veri kaynağı Ekle** ) ve **veritabanı** veri kaynağı türünü seçin. Yeni veya mevcut bir veritabanı bağlantısı ya da bir veritabanı dosyası belirtmek için istemleri izleyin.

### <a name="entity-classes"></a>Varlık sınıfları
 Veri kaynağı olarak bir Entity Framework modeli oluşturmak için önce **varlık veri modeli sihirbazını** çalıştırarak varlık sınıflarını oluşturun (**Proje**  > **yeni öğe Ekle**  > **ADO.net varlık veri modeli**).

 ![Yeni Entity Framework modeli proje öğesi](../data-tools/media/raddata-new-entity-framework-model-project-item.png "radveri yeni Entity Framework modeli proje öğesi")

 Modeli oluşturmak istediğiniz yöntemi seçin.

 ![Varlık Veri Modeli Sihirbazı](../data-tools/media/raddata-entity-data-model-wizard.png "radveri Varlık Veri Modeli Sihirbazı")

 Modeli bir veri kaynağı olarak ekleyin. Oluşturulan sınıflar, **nesneler** kategorisini seçtiğinizde **veri kaynağı Yapılandırma Sihirbazı** 'nda görüntülenir.

 ![Varlık sınıflarıyla veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "Varlık sınıflarıyla radveri veri kaynağı Yapılandırma Sihirbazı")

## <a name="data-source-for-a-service"></a>Bir hizmet için veri kaynağı
 Bir hizmetten veri kaynağı oluşturmak için, **veri kaynağı Yapılandırma Sihirbazı** 'nı çalıştırın ve **hizmet** veri kaynağı türünü seçin. Bu aslında yalnızca **hizmet başvurusu Ekle** iletişim kutusunun bir kısayoludur. Bu, ayrıca, **Çözüm Gezgini** projeye sağ tıklayıp **hizmet başvurusu Ekle**' yi seçerek de erişebilirsiniz.

 Bir hizmetten veri kaynağı oluşturduğunuzda, Visual Studio projenize bir hizmet başvurusu ekler. Visual Studio Ayrıca hizmetin döndürdüğü nesnelere karşılık gelen proxy nesnelerini de oluşturur. Örneğin, bir veri kümesi döndüren bir hizmet projenizde veri kümesi olarak temsil edilir; belirli bir türü döndüren bir hizmet, projenizde döndürülen tür olarak temsil edilir.

 Aşağıdaki hizmet türlerinden bir veri kaynağı oluşturabilirsiniz:

- WCF Veri Hizmetleri. Daha fazla bilgi için bkz. [genel bakış](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- WCF veri Hizmetleri. Daha fazla bilgi için bkz. [Visual Studio 'da Windows Communication Foundation Hizmetleri ve WCF veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).

- Web Hizmetleri.

    > [!NOTE]
    > **Veri kaynakları** penceresinde görünen öğeler, hizmetin döndürdüğü verilere bağımlıdır. Bazı hizmetler, **veri kaynağı Yapılandırma Sihirbazı** için bağlanabilir nesneler oluşturmak için yeterli bilgi sağlamayabilir. Örneğin, hizmet türsüz bir veri kümesi döndürürse, Sihirbazı tamamladığınızda **veri kaynakları** penceresinde hiçbir öğe görünmez. Bunun nedeni, türsüz veri kümelerinin bir şema sağlamamasını ve bu nedenle Sihirbazın veri kaynağını oluşturmak için yeterli bilgilere sahip olmamasından kaynaklanır.

## <a name="data-source-for-an-object"></a>Bir nesne için veri kaynağı
 **Veri kaynağı Yapılandırma Sihirbazı 'nı** çalıştırarak ve ardından **nesne** veri kaynağı türünü seçerek bir veya daha fazla ortak özellik sunan herhangi bir nesneden veri kaynağı oluşturabilirsiniz. Bir nesnenin tüm ortak özellikleri **veri kaynakları** penceresinde görüntülenir.   Entity Framework kullanıyorsanız ve bir model oluşturduysanız, uygulamanız için veri kaynağı olacak varlık sınıflarını burada bulabilirsiniz.

 **Veri nesnelerini seçin** sayfasında, bağlamak istediğiniz nesneleri bulmak için ağaç görünümündeki düğümleri genişletin. Ağaç görünümü, projeniz için ve projeniz tarafından başvurulan derlemeler ve diğer projeler için düğümler içerir.

 Ağaç görünümünde görünmeyen bir derlemede veya projede bir nesneye bağlamak istiyorsanız, **Başvuru Ekle** ' ye tıklayın ve derleme veya projeye bir başvuru eklemek Için **Başvuru Ekle iletişim kutusunu** kullanın. Başvuruyu ekledikten sonra, derleme veya proje ağaç görünümüne eklenir.

> [!NOTE]
> Nesneler ağaç görünümünde görüntülenmeden önce, nesnelerinizi içeren projeyi oluşturmanız gerekebilir.

> [!NOTE]
> Sürükle ve bırak veri bağlamayı desteklemek için, <xref:System.ComponentModel.ITypedList> veya <xref:System.ComponentModel.IListSource> arabirimini uygulayan nesnelerin varsayılan bir oluşturucusu olmalıdır. Aksi halde, Visual Studio veri kaynağı nesnesini örneklemez ve öğeyi tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint listesi için veri kaynağı
 **Veri kaynağı Yapılandırma Sihirbazı** 'nı çalıştırarak ve **SharePoint** veri kaynağı türünü seçerek SharePoint listesinden bir veri kaynağı oluşturabilirsiniz. SharePoint verileri [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] aracılığıyla kullanıma sunar, bu nedenle bir SharePoint veri kaynağı oluşturmak hizmetten veri kaynağı oluşturma ile aynıdır. **Veri kaynağı Yapılandırma Sihirbazı** 'nda **SharePoint** öğesini seçme, SharePoint sunucusuna işaret ederek sharepoint veri hizmetine bağlandığınız **hizmet başvurusu Ekle** iletişim kutusunu açar.  Bu, SharePoint SDK 'sını gerektirir.

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
