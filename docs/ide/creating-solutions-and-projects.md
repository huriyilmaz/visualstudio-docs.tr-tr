---
title: Projeler ve çözümler oluşturma
ms.date: 02/06/2018
ms.topic: how-to
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
ms.openlocfilehash: 19a836847aa01038bdbb015612c4fb4a3964d9a9
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770542"
---
# <a name="create-solutions-and-projects"></a>Projeler ve çözümler oluşturma

*Projeler* , Visual Studio 'da kaynak kodu dosyaları, bit eşlemler, simgeler ve bileşen ve hizmet başvuruları gibi uygulamanızı oluşturmak için gereken öğeleri tutar. Yeni bir proje oluşturduğunuzda, Visual Studio projeyi içeren bir *çözüm* oluşturur. İsterseniz çözüme başka yeni veya mevcut projeler ekleyebilirsiniz. Çözümler, belirli bir projeye bağlı olmayan dosyaları da içerebilir.

![Çözüm/proje hiyerarşisi](./media/vside-proj-soln.png)

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio proje oluşturma](/visualstudio/mac/create-new-projects).

Çözümlerinizi ve projelerinizi, **Çözüm Gezgini**adlı bir araç penceresinde görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsünde, iki proje içeren **Çözüm Gezgini** (**Bıkesharing. Xamarin-UWP**) içinde örnek bir çözüm gösterilmektedir: **Bıkesharing. clients. Core** ve **Bıkesharing. clients. Windows**. Her proje birden çok dosya, klasör ve başvuru içerir. Kalın yazı tipiyle proje adı *Başlangıç projem*' dir; diğer bir deyişle, uygulamayı çalıştırdığınızda Başlatan projem. Hangi projenin başlangıç projesi olduğunu belirtebilirsiniz.

![Projelerle Çözüm Gezgini](./media/vside-solution-explorer-projects.png)

Gerekli dosyaları ona ekleyerek bir projeyi kendiniz de oluşturabilirsiniz. Visual Studio size bir baş başlangıç sağlamak için proje şablonlarının bir seçimini sunar. Şablondan yeni bir proje oluşturmak, bu proje türü için temel bilgiler içeren bir proje sağlar ve gerektiğinde dosyaları yeniden adlandırabilir veya yeni ya da var olan kodu ve diğer kaynakları ekleyebilirsiniz.

Bu şekilde, Visual Studio 'da uygulama geliştirmek için çözümler ve projeler gerekli değildir. Ayrıca, git 'ten Klonladığınız veya başka bir yerde indirdiğiniz kodu da açabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Proje şablonundan proje oluşturma

Şablondan yeni bir proje oluşturma hakkında daha fazla bilgi için bkz. [Visual Studio 'da yeni proje oluşturma](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Varolan kod dosyalarından bir proje oluşturma

Bir kod kaynağı dosyası koleksiyonunuz varsa, bunları bir projeye kolayca ekleyebilirsiniz.

1. Menüde, **File**  >  **New**  >  **Varolan koddan**dosya yeni proje ' yi seçin.

1. **Varolan kod dosyalarından proje oluştur** sihirbazında, **ne tür proje oluşturmak** istediğiniz proje türünü seçin? açılan liste kutusu ve sonra **İleri** düğmesini seçin.

1. Sihirbazda, dosyaların konumuna gidin ve ardından **ad** kutusuna yeni proje için bir ad girin. İşiniz bittiğinde **son** düğmesini seçin.

> [!NOTE]
> Bu seçenek görece basit bir dosya koleksiyonu için en iyi şekilde kullanılır. Şu anda yalnızca C++, Apache Cordova, Visual Basic ve C# proje türleri desteklenir.

## <a name="add-files-to-a-solution"></a>Bir çözüme dosya ekleme

Çözüme yönelik bir Benioku dosyası veya belirli bir proje altında mantıksal olarak çözüm düzeyine ait olan diğer dosyalar gibi birden çok proje için geçerli bir dosyanız varsa, bunları çözüme ekleyebilirsiniz. Bir çözüme öğe eklemek için **Çözüm Gezgini**çözüm düğümünün bağlam (sağ tıklama) menüsünde, **Add**  >  **Yeni öğe**Ekle ' yi seçin veya **Add**  >  **varolan öğeyi**ekleyin.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>.NET Framework belirli bir sürümünü hedefleyen bir .NET projesi oluşturma

Bir .NET Framework projesi oluşturduğunuzda, projenin kullanmasını istediğiniz .NET Framework belirli bir sürümünü belirtebilirsiniz. (Bir .NET Core projesi oluşturduğunuzda Framework sürümü belirtemezsiniz.)

::: moniker range="vs-2017"

.NET Framework sürümünü belirtmek için **Yeni proje** Iletişim kutusunda **çerçeve** açılan menüsünü seçin.

![Yeni proje iletişim kutusunda çerçeve açılan menüsü](./media/vside-newproject-framework.png)

> [!NOTE]
> .NET Framework 4 ' ten önceki .NET Framework sürümlerine erişmek için sisteminizde .NET Framework 3,5 yüklü olmalıdır.

::: moniker-end

::: moniker range=">=vs-2019"

.NET Framework sürümünü belirtmek için **Yeni proje oluştur** sayfasında **çerçeve** açılan menüsünü seçin.

![Yeni proje yapılandırma içindeki çerçeve Seçicisi](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Boş çözümler oluşturma

Ayrıca, projeleri olmayan boş çözümler de oluşturabilirsiniz. Bu işlem, çözümünüzü ve projelerinizi sıfırdan oluşturmak istediğiniz durumlarda tercih edilebilir.

### <a name="to-create-an-empty-solution"></a>Boş bir çözüm oluşturmak için

1. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

::: moniker range="vs-2017"

2. Sol (**Şablonlar**) bölmesinde, genişletilmiş listede **diğer proje türleri** > **Visual Studio çözümleri** ' ni seçin.

3. Orta bölmede **boş çözüm**' ü seçin.

4. Çözümünüz için **ad** ve **konum** değerlerini girip **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. **Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** yazın.

3. **Boş çözüm** şablonunu seçin ve ardından **İleri**' ye tıklayın.

4. Çözümünüz için **ad** ve **konum** değerlerini girip **Oluştur**' u seçin.

::: moniker-end

Boş bir çözüm oluşturduktan sonra, **Proje** menüsünde **Yeni öğe Ekle** ' yi veya **Varolan öğe Ekle** ' yi seçerek yeni veya var olan projeleri veya öğeleri ekleyebilirsiniz.

Daha önce belirtildiği gibi, bir proje veya çözüme gerek duymadan kod dosyalarını da açabilirsiniz. Kodu bu şekilde geliştirme hakkında bilgi edinmek için bkz. [Visual Studio 'da proje veya çözüm olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Geçici bir proje oluşturma

(Yalnızca C# ve Visual Basic)

Oluşturun. NET tabanlı proje bir disk konumu belirtmeden, geçici bir projem. Geçici projeler, .NET projelerini denemenize olanak tanır. Geçici bir projeyle çalışırken herhangi bir zamanda kaydetmeyi veya atmayı seçebilirsiniz.

Geçici bir proje oluşturmak için önce **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **genel**' e gidin ve **oluşturulduğunda yeni projeleri kaydet** onay kutusunun işaretini kaldırın. Ardından her zamanki gibi **Yeni proje** iletişim kutusunu açın.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Bir çözümü, projeyi veya öğeyi silme

Çözümleri ve içeriklerini kalıcı olarak silebilirsiniz, ancak Visual Studio IDE 'yi kullanarak bunları kullanamazsınız. Visual Studio içindeki öğelerin silinmesi yalnızca geçerli çözüm veya projeden kaldırılır. Bir çözümü veya başka bir bileşeni sisteminizden kalıcı olarak silmek için dosya Gezgini 'ni kullanarak *. sln* ve *. suo* çözüm dosyalarını içeren klasörü silin. Ancak, bir çözümü kalıcı olarak silmeden önce, bunları yeniden yapmanız gereken herhangi bir projeyi veya dosyayı yedeklemeniz önerilir.

> [!NOTE]
> *. Suo* dosyası, varsayılan dosya Gezgini ayarları altında görüntülenmeyen gizli bir dosyadır. Gizli dosyaları göstermek için dosya Gezgini 'ndeki **Görünüm** menüsünde **gizli öğeler** onay kutusunu seçin.

### <a name="permanently-delete-a-solution"></a>Bir çözümü kalıcı olarak silme

1. **Çözüm Gezgini**, silmek istediğiniz çözümün sağ tıklama menüsünde (bağlam menüsü), **Dosya Gezgini 'nde klasörü aç**' ı seçin.

1. Dosya Gezgini 'nde, bir düzey yukarı gidin.

1. Çözümü içeren klasörü seçin ve ardından **Delete** tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [GitHub 'da Microsoft 'un açık kaynak depoları](https://github.com/Microsoft)
- [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/)
- [Proje oluşturma (Mac için Visual Studio)](/visualstudio/mac/create-new-projects)
