---
title: Çözümler & projeler oluşturma
description: yapıtları depolamak için Visual Studio çözümleri ve projeleri oluşturma ve kullanma hakkında bilgi edinin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5d40a2d76b13517ba2fba7de807e141fe9846574
ms.sourcegitcommit: 0257750be796cc46e01cebd8976f637743d29417
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2021
ms.locfileid: "130290687"
---
# <a name="create-work-with-and-delete-visual-studio-projects-and-solutions"></a>Visual Studio projeleri ve çözümleri oluşturun, bunlarla çalışın ve silin

bu makalede, uygulamalarınızı derlemek için gereken yapıtları depolamak üzere sıfırdan Visual Studio projeleri oluşturmayı ve kullanmayı öğreneceksiniz.  Visual Studio projeler hakkında bilginiz yoksa, [projelere ve çözümlere](solutions-and-projects-in-visual-studio.md)genel bakış bölümüne bakın.  Bir şablondan hızlıca bir proje oluşturmayı öğrenmek için, bkz. [Şablondan proje oluşturma](create-new-project.md).

*projeler* , kaynak kodu dosyaları, bit eşlemler, simgeler ve bileşen ve hizmet başvuruları gibi Visual Studio uygulamanızı oluşturmak için gereken öğeleri tutar. yeni bir proje oluşturduğunuzda, Visual Studio projeyi içeren bir *çözüm* oluşturur. İsterseniz çözüme başka yeni veya mevcut projeler ekleyebilirsiniz. Ayrıca, [boş veya boş çözümler](#create-empty-solutions)oluşturabilirsiniz. Çözümler, belirli bir projeye bağlı olmayan dosyaları da içerebilir.

![Çözüm ve proje hiyerarşisini gösteren diyagram.](./media/vside-proj-soln.png)

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio proje oluşturma](/visualstudio/mac/create-new-projects).

Çözümlerinizi ve projelerinizi, **Çözüm Gezgini** adlı bir araç penceresinde görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsünde, iki proje içeren **Çözüm Gezgini** (**Bıkesharing. Xamarin-UWP**) içinde örnek bir çözüm gösterilmektedir: **Bıkesharing. clients. Core** ve **bıkesharing. clients. Windows**. Her proje birden çok dosya, klasör ve başvuru içerir. Kalın yazı tipiyle proje adı *Başlangıç projem*' dir; diğer bir deyişle, uygulamayı çalıştırdığınızda Başlatan projem. Hangi projenin başlangıç projesi olduğunu belirtebilirsiniz.

![İki projeyle Çözüm Gezgini ekran görüntüsü.](./media/vside-solution-explorer-projects.png)

gerekli dosyaları ekleyerek kendinize bir proje oluşturabilirsiniz; Visual Studio, size baş bir başlangıç sağlamak için proje şablonlarının bir seçimini sunmaktadır. Şablondan yeni bir proje oluşturmak, bu proje türü için temel bilgiler içeren bir proje sağlar ve gerektiğinde dosyaları yeniden adlandırabilir veya yeni ya da var olan kodu ve diğer kaynakları ekleyebilirsiniz.

Bu şekilde, çözümler ve projeler Visual Studio uygulama geliştirmek için gerekli değildir. Ayrıca, git 'ten Klonladığınız veya başka bir yerde indirdiğiniz kodu da açabilirsiniz. daha fazla bilgi için bkz. [proje veya çözüm olmadan Visual Studio kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Proje şablonundan proje oluşturma

Yeni bir proje oluşturmak için şablon seçme hakkında bilgi için, bkz. [Visual Studio yeni proje oluşturma](create-new-project.md). Ayrıca, sıfırdan oluşturulmuş bir proje ve çözüm örneği için adım adım yönergeler ve örnek kodla birlikte, bkz. [projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md).

## <a name="create-a-project-from-existing-code-files"></a>Varolan kod dosyalarından bir proje oluşturma

Bir kod kaynağı dosyası koleksiyonunuz varsa, bunları bir projeye kolayca ekleyebilirsiniz.

1. menüde,   >    >  **varolan koddan** dosya yeni Project ' yi seçin.

1. **varolan kod dosyalarından Project oluştur** sihirbazında, **ne tür proje oluşturmak istersiniz?** açılan liste kutusunda istediğiniz proje türünü seçin ve sonra **ileri** düğmesini seçin.

1. Sihirbazda, dosyaların konumuna gidin ve ardından **ad** kutusuna yeni proje için bir ad girin. İşiniz bittiğinde **son** düğmesini seçin.

> [!NOTE]
> Bu seçenek görece basit bir dosya koleksiyonu için en iyi şekilde kullanılır. şu anda yalnızca C++, Apache Cordova, Visual Basic ve C# proje türleri desteklenir.

## <a name="add-files-to-a-solution"></a>Bir çözüme dosya ekleme

Çözüme yönelik bir Benioku dosyası veya belirli bir proje altında mantıksal olarak çözüm düzeyine ait olan diğer dosyalar gibi birden çok proje için geçerli bir dosyanız varsa, bunları çözüme ekleyebilirsiniz. Bir çözüme öğe eklemek için **Çözüm Gezgini** çözüm düğümünün bağlam (sağ tıklama) menüsünde,   >  **Yeni öğe** Ekle ' yi seçin veya   >  **varolan öğeyi** ekleyin.

> [!TIP]
> Çözüm dosyası, Visual Studio projelerin düzenlenmesine yönelik bir yapıdır. Bu bilgilerin durumunu iki dosyada içerir: *. sln* (metin tabanlı, paylaşılan) dosya ve bir *. suo* (ikili, gizli, kullanıcıya özel çözüm seçenekleri) dosyası. Bu nedenle, çözüm kopyalanmaları ve yeniden adlandırılması gereken bir şey değildir; Bunun yerine, yeni bir çözüm oluşturmak ve var olan öğeleri buna eklemek en iyisidir.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>.NET Framework belirli bir sürümünü hedefleyen bir .NET projesi oluşturma

bir .NET Framework projesi oluşturduğunuzda, projenin kullanmasını istediğiniz .NET Framework belirli bir sürümünü belirtebilirsiniz. (Bir .NET Core projesi oluşturduğunuzda Framework sürümü belirtemezsiniz.)

::: moniker range="vs-2017"

.NET Framework sürümünü belirtmek için **yeni Project** iletişim kutusunda **çerçeve** açılan menüsünü seçin.

![yeni Project iletişim kutusunda çerçeve açılan ekranının ekran görüntüsü.](./media/vside-newproject-framework.png)

> [!NOTE]
> .NET Framework 4 ' ten önceki .NET Framework sürümlerine erişmek için sisteminizde .NET Framework 3,5 yüklü olmalıdır.

::: moniker-end

::: moniker range=">=vs-2019"

.NET Framework sürümünü belirtmek için **yeni proje oluştur** sayfasında **çerçeve** açılan menüsünü seçin.

![' Yeni proje Yapılandır ' iletişim kutusunda çerçeve seçicinin ekran görüntüsü.](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Boş çözümler oluşturma

Ayrıca, projeleri olmayan boş çözümler de oluşturabilirsiniz. Bu işlem, çözümünüzü ve projelerinizi sıfırdan oluşturmak istediğiniz durumlarda tercih edilebilir.

### <a name="to-create-an-empty-solution"></a>Boş bir çözüm oluşturmak için

1. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

::: moniker range="vs-2017"

2. sol (**şablonlar**) bölmesinde, genişletilmiş listedeki çözümler **Visual Studio diğer Project türleri** ' ni seçin >  .

3. Orta bölmede **boş çözüm**' ü seçin.

4. Çözümünüz için **ad** ve **konum** değerlerini girip **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. **Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** yazın.

3. **Boş çözüm** şablonunu seçin ve ardından **İleri**' ye tıklayın.

4. Çözümünüz için **ad** ve **konum** değerlerini girip **Oluştur**' u seçin.

::: moniker-end

boş bir çözüm oluşturduktan sonra, yeni **öğe** ekle ' yi veya **Project** menüsünde **varolan öğe ekle** ' yi seçerek yeni veya mevcut projeleri veya öğeleri ekleyebilirsiniz.

Daha önce belirtildiği gibi, bir proje veya çözüme gerek duymadan kod dosyalarını da açabilirsiniz. kodu bu şekilde geliştirme hakkında bilgi edinmek için bkz. [projeler veya çözümler olmadan Visual Studio kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Geçici bir proje oluşturma

(yalnızca C# ve Visual Basic)

Oluşturun. NET tabanlı proje bir disk konumu belirtmeden, geçici bir projem. Geçici projeler, .NET projelerini denemenize olanak tanır. Geçici bir projeyle çalışırken herhangi bir zamanda kaydetmeyi veya atmayı seçebilirsiniz.

Geçici bir proje oluşturmak için önce **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **genel**' e gidin ve **oluşturulduğunda yeni projeleri kaydet** onay kutusunun işaretini kaldırın. sonra **yeni Project** iletişim kutusunu her zamanki gibi açın.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Bir çözümü, projeyi veya öğeyi silme

Visual Studio çözümleri, projeleri veya öğeleri silmek ya da kaldırmak için sağ tıklama bağlam menüsünü kullanabilirsiniz, ancak bu yalnızca geçerli çözüm veya projeden kaldırılır.

bir çözümü veya diğer bileşenleri sisteminizden kalıcı olarak silmek için, *. sln* ve *. suo* çözüm dosyalarını içeren klasörü silmek için Windows 'de **dosya gezgini** 'ni kullanın. (Bir çözümü silmeden önce, projelerinizi ve dosyalarınızı tekrar ihtiyacınız olduğunda yedeklemek isteyebilirsiniz.)

> [!NOTE]
> *. Suo* dosyası, varsayılan dosya Gezgini ayarları altında görüntülenmeyen gizli bir dosyadır. Gizli dosyaları göstermek için dosya Gezgini 'ndeki **Görünüm** menüsünde **gizli öğeler** onay kutusunu seçin.

### <a name="permanently-delete-a-solution"></a>Bir çözümü kalıcı olarak silme

Windows dosya gezginine, Visual Studio Çözüm Gezgini kullanarak erişebilirsiniz. Aşağıdaki adımları uygulayın:

1. **Çözüm Gezgini**, silmek istediğiniz çözümün sağ tıklama menüsünde (bağlam menüsü), **Dosya Gezgini 'nde klasörü aç**' ı seçin.

1. Dosya Gezgini 'nde, bir düzey yukarı gidin.

1. Çözümü içeren klasörü seçin ve ardından **Delete** tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [Visual Studio filtrelenmiş çözümler](filtered-solutions.md)
- [GitHub Microsoft 'un açık kaynak depoları](https://github.com/Microsoft)
- [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/)