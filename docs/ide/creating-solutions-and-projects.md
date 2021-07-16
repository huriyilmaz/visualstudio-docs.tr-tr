---
title: Proje ve & oluşturma
description: Yapıtları depolamak için Visual Studio çözümleri ve projeleri oluşturma ve kullanma hakkında bilgi edinin.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 06/14/2021
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f05a940787c2ab601b0b29db8ec5004c621a16b8
ms.sourcegitcommit: d856c46d78638be609e7045621ed1bd7521a6dcc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114283852"
---
# <a name="create-work-with-and-delete-visual-studio-projects-and-solutions"></a>Projeleri ve çözümleri oluşturma, Visual Studio ve silme

Bu makalede, uygulamalarınızı derlemek için ihtiyacınız olan yapıtları depolamak için Visual Studio projelerini oluşturma ve kullanma hakkında bilgi edinebilirsiniz.  Visual Studio'daki projeler hakkında bilgi sahibi değil Visual Studio projelere ve çözümlere [genel bakışa bakın.](solutions-and-projects-in-visual-studio.md)  Şablondan hızla proje oluşturma hakkında bilgi edinmek için [bkz. Şablondan proje oluşturma.](create-new-project.md)

*Projeler,* kaynak kod dosyaları, bit eşlemler, simgeler Visual Studio bileşen ve hizmet başvuruları gibi uygulamalarınızı derlemek için gereken öğeleri içerir. Yeni bir proje oluştururken, Visual Studio içeren *bir* çözüm oluşturur. Daha sonra, 2009'da 2000'den fazla yeni veya mevcut proje 5.000'e 500000000000000000 Boş veya boş [çözümler de oluşturabilirsiniz.](#create-empty-solutions) Çözümler belirli bir projeye bağlı olmayan dosyaları da içerebilir.

![Çözüm ve proje hiyerarşisini gösteren diyagram.](./media/vside-proj-soln.png)

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio.](/visualstudio/mac/create-new-projects)

Çözümlerinizi ve projelerinizi Çözüm Gezgini adlı bir **araç penceresinde görüntüebilirsiniz.** Aşağıdaki ekran görüntüsünde, **Çözüm Gezgini** (**BikeSharing.Xamarin-UWP**) içinde **bikeSharing.Clients.Core** ve **BikeSharing.Clients.Windows**. Her proje birden çok dosya, klasör ve başvuru içerir. Kalın yazıyla proje adı başlangıç *projesidir;* başka bir ifadeyle, uygulamayı çalıştırarak başlayan projedir. Hangi projenin başlangıç projesi olduğunu belirterek.

![İki proje Çözüm Gezgini ekran görüntüsü.](./media/vside-solution-explorer-projects.png)

Bir projeyi gerekli dosyaları ekleyerek kendiniz oluşturabilirsiniz ancak Visual Studio size başlangıç yapmak için bir proje şablonu seçimi sunar. Şablondan yeni bir proje oluşturmak, size bu proje türü için temel öneme sahip bir proje sağlar ve dosyaları yeniden adlandırabilir veya gerektiğinde yeni ya da mevcut kodu ve diğer kaynakları ekebilirsiniz.

Bu nedenle, çözüm ve projelerin uygulama geliştirmek için gerekli Visual Studio. Git'den kopyalanmış veya başka bir yere indirdiğiniz kodu da açabilirsiniz. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="create-a-project-from-a-project-template"></a>Proje şablonundan proje oluşturma

Yeni proje oluşturmak için şablon seçme hakkında daha fazla bilgi için [bkz.](create-new-project.md)Visual Studio. Sıfırdan oluşturulan bir proje ve çözüm örneği için, adım adım yönergeler ve örnek kod ile tamamlandıktan sonra, bkz. Projelere ve [çözümlere giriş.](../get-started/tutorial-projects-solutions.md)

## <a name="create-a-project-from-existing-code-files"></a>Mevcut kod dosyalarından proje oluşturma

Bir kod kaynak dosyaları koleksiyonunuz varsa, bunları bir projeye kolayca ekleme.

1. Menüde Dosya Yeni **Dosya'Project**  >    >  **Var Olan Koddan'ı seçin.**

1. Mevcut **Kod Project** Oluştur sihirbazında, Ne tür bir proje oluşturmak ister **misiniz?** açılan liste kutusunda istediğiniz proje türünü seçin ve ardından Sonraki **düğmesini** seçin.

1. Sihirbazda dosyaların bulunduğu konuma göz atarak Ad kutusuna yeni proje için bir **ad** girin. Bitirerek Son **düğmesini** seçin.

> [!NOTE]
> Bu seçenek, görece basit bir dosya koleksiyonu için en iyi şekilde çalışır. Şu anda yalnızca C++, Apache Cordova, Visual Basic ve C# proje türleri de destekleni.

## <a name="add-files-to-a-solution"></a>Çözüme dosya ekleme

Çözüm için beni oku dosyası gibi birden çok projeye uygulanan bir dosyanız veya belirli bir proje altında değil, mantıksal olarak çözüm düzeyinde yer alan diğer dosyalar varsa, bunları çözümün kendisine eklemek için kullanabilirsiniz. Bir çözüme öğe eklemek için, Çözüm Gezgini'daki çözüm düğümünün bağlam (sağ tıklama) menüsünde **Yeni** Öğe Ekle'yi veya Var Olan Öğeyi  >   **Ekle'yi**  >  **seçin.**

> [!TIP]
> Çözüm dosyası, bir çözüm dosyasındaki projeleri düzenlemeye Visual Studio. Bu bilgilerin durumunu iki dosyada içerir: *bir .sln* (metin tabanlı, paylaşılan) dosyası ve *bir .suo* (ikili, gizli, kullanıcıya özgü çözüm seçenekleri) dosyası. Bu nedenle çözüm kopyalanır ve yeniden adlandırılamaz; Bunun yerine, en iyisi yeni bir çözüm oluşturmak ve var olan öğeleri buna eklemektir.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Uygulamanın belirli bir sürümünü hedef alan bir .NET .NET Framework

Yeni bir .NET Framework oluşturdukta, projenin .NET Framework istediğiniz belirli bir sürümü belirtsiniz. (Bir .NET Core projesi oluşturdukta çerçeve sürümü belirtmezsiniz.)

::: moniker range="vs-2017"

Yeni sürüm .NET Framework belirtmek için Yeni  sürüm iletişim kutusunda Framework **açılan Project** seçin.

![Yeni uygulama iletişim kutusundaki Framework açılan Project görüntüsü.](./media/vside-newproject-framework.png)

> [!NOTE]
> 4'.NET Framework önceki sürümlere erişmek için sisteminize .NET Framework 3.5 .NET Framework gerekir.

::: moniker-end

::: moniker range=">=vs-2019"

Yeni bir .NET Framework belirtmek için Yeni  proje oluştur sayfasında Framework **açılan menüsünü** seçin.

!['Yeni projeyi yapılandır' iletişim kutusundaki Çerçeve seçicinin ekran görüntüsü.](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Boş çözümler oluşturma

Ayrıca, projesiz boş çözümler de oluşturabilirsiniz. Çözüm ve projelerinizi sıfırdan oluşturmak istediğiniz durumlarda bu tercih edilebilir.

### <a name="to-create-an-empty-solution"></a>Boş bir çözüm oluşturmak için

1. Menü çubuğunda Dosya Yeni'yi **seçin**  >  **ve**  >  **Project.**

::: moniker range="vs-2017"

2. Sol bölmede (**Şablonlar**) genişletilmiş listede Diğer **Project Türleri** > **Visual Studio Çözümler'i** seçin.

3. Orta bölmede Boş **Çözüm'i seçin.**

4. **Çözümünüz** için **Ad** ve Konum değerlerini girin ve tamam'ı **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Yeni **proje oluştur sayfasında** arama kutusuna **çözüm** yazın.

3. Boş Çözüm **şablonunu seçin** ve ardından Sonraki'ye **tıklayın.**

4. **Çözümünüz** için **Ad** ve Konum değerlerini girin ve oluştur'a **basın.**

::: moniker-end

Boş bir çözüm oluşturdukta, yeni veya mevcut projeleri ya  da öğeleri  eklemek için Yeni Öğe Ekle'yi veya Yeni Öğe Ekle'yi **seçerek** Project ekleyebilirsiniz.

Daha önce belirtildiği gibi, bir projeye veya çözüme gerek kalmadan kod dosyalarını açabilirsiniz. Bu şekilde kod geliştirme hakkında bilgi edinmek için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Geçici proje oluşturma

(Yalnızca C# Visual Basic)

Bir sanız. Net tabanlı proje, disk konumu belirtmeden geçici bir projedir. Geçici projeler .NET projeleriyle denemeler sağlar. Geçici bir projeyle çalışırken istediğiniz zaman projeyi kaydedebilir veya atabilirsiniz.

Geçici bir proje oluşturmak için önce Araçlar Seçenekler Projeleri ve Çözümler Genel'e gidin ve Yeni projeleri oluşturulduğunda  >    >    >  kaydet onay **kutusunun işaretini** kaldırın. Ardından Her **zamanki Project** Yeni Dosya iletişim kutusunu açın.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Çözümü, projeyi veya öğeyi silme

Sağ tıklama bağlam menüsünü kullanarak Visual Studio'daki çözümleri, projeleri veya öğeleri silebilir veya kaldırabilirsiniz. Ancak bu, bunları yalnızca geçerli çözümden veya projeden kaldırır.

Bir çözümü veya diğer bileşenleri sisteminize kalıcı  olarak silmek için Dosya Gezgini'Windows *.sln* ve *.suo* çözüm dosyalarını içeren klasörü silmek için kullanın. (Bir çözümü smeden önce, yeniden ihtiyacınız olursa projelerinizi ve dosyalarınızın da aynı şekilde geri yüklemesi iyi olabilir.)

> [!NOTE]
> *.suo* dosyası, varsayılan dosya adı ayarları altında görüntülenmez Dosya Gezgini dosyasıdır. Gizli dosyaları göstermek için, **Dosya Gezgini'daki** Görünüm menüsünde Gizli Öğeler **onay** kutusunu seçin.

### <a name="permanently-delete-a-solution"></a>Çözümü kalıcı olarak silme

Windows'Dosya Gezgini Çözüm Gezgini kullanarak Visual Studio. Aşağıdaki adımları uygulayın:

1. Bu **Çözüm Gezgini,** silmek istediğiniz çözümün sağ tıklama menüsünde (bağlam menüsü) klasör **aç'ı** Dosya Gezgini.

1. Bu Dosya Gezgini bir düzey yukarı gidin.

1. Çözümü içeren klasörü seçin ve Sil **tuşuna** basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [Verilerde filtrelenmiş Visual Studio](filtered-solutions.md)
- [Microsoft'un açık kaynak depoları GitHub](https://github.com/Microsoft)
- [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/)
- [IDE hatalarını Visual Studio kaynakları](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
