---
title: Projeler ve çözümler oluşturma
ms.date: 02/06/2018
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 503b343299f7b30e9f5e834099274215b262a635
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301820"
---
# <a name="create-solutions-and-projects"></a>Projeler ve çözümler oluşturma

*Projeler,* uygulamanızı Visual Studio'da oluşturmak için gereken kaynak kod dosyaları, bit eşlemler, simgeler ve bileşen ve hizmet başvuruları gibi öğeleri tutar. Yeni bir proje oluşturduğunuzda, Visual Studio projeyi içeren bir *çözüm* oluşturur. Daha sonra isterseniz çözüme başka yeni veya varolan projeler ekleyebilirsiniz. Çözümler, belirli bir projeye bağlı olmayan dosyalar da içerebilir.

![Çözüm/proje hiyerarşisi](./media/vside-proj-soln.png)

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için](/visualstudio/mac/create-new-projects)bkz.

Çözümlerinizi ve projelerinizi **Çözüm Gezgini**adlı bir araç penceresinde görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsü Çözüm **Gezgini'nde** **(BikeSharing.Xamarin-UWP)** iki proje içeren örnek bir çözüm gösterir: **BikeSharing.Clients.Core** ve **BikeSharing.Clients.Windows**. Her proje birden çok dosya, klasör ve başvuru içerir. Kalın proje adı *başlangıç projesidir;* diğer bir şekilde, uygulamayı çalıştırdığınızda başlayan projedir. Başlangıç projesinin hangi proje olduğunu belirtebilirsiniz.

![Projelerle Çözüm Gezgini](./media/vside-solution-explorer-projects.png)

Bir projeyi gerekli dosyaları ekleyerek kendiniz oluşturabilirsiniz, ancak Visual Studio size bir başlangıç sağlamak için bir dizi proje şablonu sunar. Şablondan yeni bir proje oluşturmak, size bu proje türü için gerekli olan bir proje verir ve dosyaları yeniden adlandırabilir veya gerektiğinde yeni veya varolan kod ve diğer kaynakları ekleyebilirsiniz.

Bununla da, Visual Studio'da uygulama geliştirmek için çözümler ve projelere gerek yoktur. Ayrıca, Git'ten klonladığınız veya başka bir yerden indirdiğiniz kodu da açabilirsiniz. Daha fazla bilgi için visual [studio'da proje veya çözüm olmadan kod geliştir'e](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)bakın.

## <a name="create-a-project-from-a-project-template"></a>Proje şablonundan proje oluşturma

Şablondan yeni bir proje oluşturma hakkında bilgi için visual [studio'da yeni bir proje oluşturma](create-new-project.md)bilgisine bakın.

## <a name="create-a-project-from-existing-code-files"></a>Varolan kod dosyalarından proje oluşturma

Kod kaynağı dosyaları koleksiyonunuz varsa, bunları kolayca bir projeye ekleyebilirsiniz.

1. Menüde,**Varolan Koddan****Yeni** > Proje **Dosyasını** > seçin.

1. **Varolan Kod Dosyaları'ndan Proje Oluştur** sihirbazında, **ne tür bir proje oluşturmak istiyorsunuz?** açılan liste kutusunda istediğiniz proje türünü seçin ve ardından **Sonraki** düğmesini seçin.

1. Sihirbazda, dosyaların konumuna göz atın ve ardından **Ad** kutusuna yeni proje için bir ad girin. İşlem bittiğinde, **Bitiş** düğmesini seçin.

> [!NOTE]
> Bu seçenek, nispeten basit bir dosya koleksiyonu için en iyi şekilde çalışır. Şu anda yalnızca C++, Apache Cordova, Visual Basic ve C# proje türleri desteklenir.

## <a name="add-files-to-a-solution"></a>Çözüme dosya ekleme

Çözüm için okuma dosyası veya belirli bir proje altında değil de mantıksal olarak çözüm düzeyinde ait diğer dosyalar gibi birden çok projeye uygulanan bir dosyanız varsa, bunları çözümün kendisine ekleyebilirsiniz. Çözüme öğe eklemek için, **Çözüm Gezgini'ndeki**çözüm düğümünün bağlam (sağ tıklatma) menüsünde**Yeni Öğe** **Ekle'yi** > veya**Varolan Öğe Ekle'yi** **Add** > seçin.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>.NET Çerçevesi'nin belirli bir sürümünü hedefleyen bir .NET projesi oluşturma

Bir .NET Framework projesi oluşturduğunuzda, .NET Framework'ün , projenin kullanmasını istediğiniz belirli bir sürümünü belirtebilirsiniz. (Bir .NET Core projesi oluşturduğunuzda, bir çerçeve sürümü belirtmezsiniz.)

::: moniker range="vs-2017"

.NET Framework sürümünü belirtmek için, **Yeni Proje** iletişim kutusundaki **Framework** açılır menüsünü seçin.

![Yeni Proje iletişim kutusunda çerçeve açılır](./media/vside-newproject-framework.png)

> [!NOTE]
> .NET Framework 4'ten önce .NET Framework sürümlerine erişmek için sisteminizde .NET Framework 3.5 yüklü olmalıdır.

::: moniker-end

::: moniker range=">=vs-2019"

.NET Framework sürümünü belirtmek için, **yeni bir proje oluştur** **sayfasındaki Framework** açılır menüsünü seçin.

![Yeni proje yapılandırmada çerçeve seçici](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Boş çözümler oluşturun

Ayrıca, projesi olmayan boş çözümler de oluşturabilirsiniz. Bu, çözümünüzü ve projelerinizi sıfırdan oluşturmak istediğiniz durumlarda tercih edilebilir.

### <a name="to-create-an-empty-solution"></a>Boş bir çözüm oluşturmak için

1. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > 

::: moniker range="vs-2017"

2. Soldaki **(Şablonlar)** bölmesinde, genişletilmiş listede **Diğer Proje Türleri** > **Görsel Stüdyo Çözümleri'ni** seçin.

3. Orta bölmede Boş **Çözüm'u**seçin.

4. Çözümünüz için **Ad** ve **Konum** değerlerini girin ve ardından **Tamam'ı**seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Yeni **bir proje oluştur** **sayfasında, çözüm** arama kutusuna yazın.

3. Boş **Çözüm** şablonu'nu seçin ve sonra **İleri'yi**tıklatın.

4. Çözümünüz için **Ad** ve **Konum** değerlerini girin ve ardından **Oluştur'u**seçin.

::: moniker-end

Boş bir çözüm oluşturduktan sonra, **Proje** menüsünde Yeni Öğe **Ekle** veya **Varolan Öğe Ekle'yi** seçerek yeni veya varolan projeleri veya öğeleri ekleyebilirsiniz.

Daha önce de belirtildiği gibi, bir proje veya çözüme gerek kalmadan kod dosyalarını da açabilirsiniz. Bu şekilde kod geliştirme hakkında bilgi edinmek için visual [studio'da proje veya çözüm olmadan kod geliştir'e](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)bakın.

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Geçici bir proje oluşturma

(Yalnızca C# ve Visual Basic)

Bir . NET tabanlı proje bir disk konumu belirtmeden, geçici bir projedir. Geçici projeler .NET projeleri ile deneme yapmanızı sağlar. Geçici bir projeyle çalışırken istediğiniz zaman, projeyi kaydetmeyi veya atmayı seçebilirsiniz.

Geçici bir proje oluşturmak için önce **Araçlar** > **Seçenekleri** > **Projeleri ve Çözümleri** > **Genel'e**gidin ve onay kutusu **oluşturulduğunda yeni projeleri kaydet'in** denetimini kaldırın. Ardından **Yeni Proje** iletişim kutusunu her zamanki gibi açın.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Bir çözümü, projeyi veya öğeyi silme

Visual Studio IDE'yi kullanarak çözümleri ve içeriklerini kalıcı olarak silebilirsiniz. Visual Studio içindeki öğeleri silerse, öğeleri yalnızca geçerli çözümden veya projeden kaldırır. Bir çözümü veya başka bir bileşeni sisteminizden kalıcı olarak silmek için *.sln* ve *.suo* çözüm dosyalarını içeren klasörü silmek için Dosya Gezgini'ni kullanın. Ancak, bir çözümü kalıcı olarak silmeden önce, yeniden gereksinim duymanız durumunda projeleri veya dosyaları yedeklemeniz önerilir.

> [!NOTE]
> *.suo* dosyası, varsayılan Dosya Gezgini ayarları altında görüntülenmeyen gizli bir dosyadır. Gizli dosyaları göstermek için Dosya Gezgini'ndeki **Görünüm** menüsünde **Gizli Öğeler** onay kutusunu seçin.

### <a name="permanently-delete-a-solution"></a>Bir çözümü kalıcı olarak silme

1. **Solution**Explorer'da, silmek istediğiniz çözümün sağ tıklama menüsünde (bağlam menüsü), **Dosya Gezgini'nde Klasörü Aç'ı**seçin.

1. Dosya Gezgini'nde, bir düzeyyukarı gidin.

1. Çözümü içeren klasörü seçin ve sonra **Sil** tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [Microsoft'un GitHub'daki açık kaynak depoları](https://github.com/Microsoft)
- [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/)
- [Projeler oluşturun (Mac için Visual Studio)](/visualstudio/mac/create-new-projects)
