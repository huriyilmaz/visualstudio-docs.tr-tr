---
title: Yeni bir proje oluşturun
ms.date: 03/19/2019
ms.topic: conceptual
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77a6a33a1dde4d779a56c9ee559ecfd3b20dfbfb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585476"
---
# <a name="create-a-new-project-in-visual-studio"></a>Visual Studio 'da yeni proje oluşturma

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Yeni proje iletişim kutusunu aç

Visual Studio 2017 ' de yeni bir proje oluşturmanın birden çok yolu vardır. Başlangıç sayfasında, proje **şablonları ara** kutusuna bir proje şablonunun adını yazabilir veya yeni proje **Oluştur** bağlantısını seçerek **Yeni proje** iletişim kutusunu açabilirsiniz. Başlangıç sayfasından sonra, menü çubuğunda **dosya** > **Yeni** > **projesi** ' ni seçip araç çubuğunda **Yeni proje** düğmesine tıklayabilirsiniz.

![Yeni > projesi > sayfa ve dosya başlatma](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Şablon türü seçin

İçinde **yeni proje** iletişim kutusu, kullanılabilir proje şablonları görünür altında bir listede **şablonları** kategorisi. Şablonları Visual gibi dil ve proje türü programlama tarafından düzenlenir C#, JavaScript ve Azure Data Lake.

![Yeni Proje iletişim kutusu](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Görüntülenen listeden kullanılabilir diller ve proje şablonları, kullanmakta olduğunuz Visual Studio ve yüklü iş yükleri sürümüne bağlıdır. Ek iş yüklerini nasıl yükleyeceğiniz hakkında bilgi edinmek için bkz. [iş yüklerini ve bileşenleri ekleyerek veya kaldırarak Visual Studio 'Yu değiştirme](../install/modify-visual-studio.md).

Dil adının yanındaki üçgeni tıklatıp ardından bir proje kategorisi (Windows Masaüstü gibi) seçerek kullanmak istediğiniz programlama diline ait şablonların listesini görüntüleyin.

Aşağıdaki görüntüde, Visual C# .NET Core projeleri için kullanılabilir proje şablonları gösterilmektedir:

![Proje şablonları](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Projenizi yapılandırma

Yeni proje için bir ad girin **adı** kutusu. Projeyi bilgisayarınızda varsayılan konuma kaydedebilir ya da başka bir konum bulmak için **tarayıcı** düğmesine tıklayabilirsiniz. Ayrıca, bir çözüm adı seçebilir veya yeni projeyi bir git deposuna ekleyebilirsiniz ( **kaynak denetimine Ekle**' yi seçerek).

Çözümü ve projeyi oluşturmak için **Tamam** ' ı tıklatın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Yeni proje oluştur sayfasını açın

Visual Studio 2019 ' de yeni bir proje oluşturmanın birden çok yolu vardır. Visual Studio 'yu ilk kez açtığınızda, başlangıç penceresi görünür ve buradan **Yeni proje oluştur**seçeneğini belirleyebilirsiniz.

![VS 2019 ' de başlangıç penceresinden yeni bir proje oluştur](media/vs-2019/start-window-create-new-project.png)

Visual Studio geliştirme ortamı zaten açıksa, menü çubuğunda **dosya** > **Yeni** > **Proje** ' yi seçerek veya araç çubuğundaki **Yeni proje** düğmesine tıklayarak yeni bir proje oluşturabilirsiniz.

![Visual Studio 2019 ' de yeni proje düğmesi](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Şablon türü seçin

**Yeni proje oluştur** sayfasında, son seçtiğiniz şablonların listesi solda görüntülenir. Şablonlar *en son kullanılanlar*tarafından sıralanır.

Son kullanılan şablonlardan seçim yapmadıysanız, tüm kullanılabilir proje şablonlarını **dile** göre C# (örneğin, C++veya), **Platform** (örneğin, Windows veya Azure) ve **proje türünü** (örneğin, masaüstü veya Web) göre filtreleyebilirsiniz. Şablonları daha fazla filtrelemek için arama kutusuna arama metni de girebilirsiniz, örneğin, **ASP.net**.

![Visual Studio 2019 'de proje şablonu filtreleri](media/vs-2019/create-new-project-filters.png)

Her şablon altında görüntülenen Etiketler üç açılan listeye (dil, platform ve proje türü) karşılık gelir.

> [!TIP]
> Aradığınız şablonu görmüyorsanız, Visual Studio için bir iş yükünüz eksik olabilir. Örneğin, **Azure geliştirme** veya **.NET ile mobil geliştirme**gibi ek iş yükleri yüklemek için Visual Studio yükleyicisi açmak üzere **daha fazla araç ve özellik yüklemesi** bağlantısına tıklayın. Buradan, yüklemek istediğiniz iş yüklerini seçin ve ardından **Değiştir**' i seçin. Bundan sonra, ek proje şablonları arasından seçim yapabileceğiniz şekilde sunulacaktır.
>
> ![VS 2019 ' de daha fazla araç ve özellik yüklemesi](media/vs-2019/install-more-tools-features.png)

Bir şablon seçin ve ardından **İleri**' ye tıklayın.

## <a name="configure-your-project"></a>Projenizi yapılandırma

**Yeni projenizi yapılandırma** sayfasında projenize (ve çözümüne) ad vermek için kullanabileceğiniz seçenekler bulunur, bir disk konumu seçebilir ve bir çerçeve sürümü (seçtiğiniz şablona uygunsa) seçin.

![VS 2019 ' de yeni proje sayfanızı yapılandırma](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Visual Studio 'da zaten açık bir proje veya çözümünüz varsa yeni bir proje oluşturursanız, ek bir yapılandırma seçeneği kullanılabilir. Yeni bir çözüm oluşturmayı veya zaten açık olan çözüme yeni projeyi eklemeyi seçebilirsiniz.
>
> ![VS 2019 ' de yeni çözüm oluşturma veya var olan çözüme ekleme](media/vs-2019/configure-new-project-solution.png)

Yeni projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Çözüme ek projeler ekleme

Bir çözüme ek bir proje eklemek istiyorsanız **Çözüm Gezgini** çözüm düğümüne sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler oluşturma](creating-solutions-and-projects.md)
