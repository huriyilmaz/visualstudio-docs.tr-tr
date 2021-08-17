---
title: Yeni proje oluşturma
description: Visual Studio yeni bir proje oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/23/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8f885922e5b383d81d1d7c31faff43e569dc6732
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109545"
---
# <a name="create-a-new-project-in-visual-studio"></a>Visual Studio yeni bir proje oluşturun

bu makalede, bir şablondan Visual Studio ' de hızlı bir şekilde yeni bir proje oluşturmayı göstereceğiz.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>yeni Project iletişim kutusunu açın

Visual Studio 2017 ' de yeni bir proje oluşturmanın birden çok yolu vardır. başlangıç sayfasında, **proje şablonları ara** kutusuna bir proje şablonunun adını yazabilir veya yeni **proje oluştur** bağlantısını seçerek **yeni Project** iletişim kutusunu açabilirsiniz. başlangıç sayfasından, menü çubuğunda **dosya**  >  **yeni**  >  **Project** ' yi de seçebilir veya araç çubuğunda **yeni Project** düğmesine tıklayabilirsiniz.

![dosya > yeni > Project seçenekler seçiliyken Visual Studio içindeki menü çubuğunun ekran görüntüsü.](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Şablon türü seçin

**yeni Project** iletişim kutusunda, kullanılabilir proje şablonları **şablonlar** kategorisi altındaki bir listede görüntülenir. Şablonlar programlama diline ve Visual C#, JavaScript ve Azure Data Lake gibi proje türüne göre düzenlenir.

![yeni Project iletişim kutusunun yüklü şablonlar listesini gösteren ekran görüntüsü.](./media/vside-newproject-templates-list.png)

> [!NOTE]
> görüntülenen kullanılabilir dillerin ve proje şablonlarının listesi, çalıştırdığınız Visual Studio sürümüne ve yüklenen iş yüklerine bağlıdır. ek iş yüklerini nasıl yükleyeceğiniz hakkında bilgi edinmek için bkz. [iş yüklerini ve bileşenleri ekleyerek veya kaldırarak Visual Studio değiştirme](../install/modify-visual-studio.md).

dil adının yanındaki üçgeni tıklatıp ardından bir proje kategorisi (Windows masaüstü) seçerek kullanmak istediğiniz programlama diline ait şablonların listesini görüntüleyin.

Aşağıdaki görüntüde, Visual C# .NET Core projeleri için kullanılabilir proje şablonları gösterilmektedir:

![aralarından seçim yapabileceğiniz proje şablonlarını listeleyen yeni Project iletişim kutusunun ekran görüntüsü.](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Projenizi yapılandırma

**Ad** kutusuna yeni proje için bir ad girin. Projeyi bilgisayarınızda varsayılan konuma kaydedebilir ya da başka bir konum bulmak için **tarayıcı** düğmesine tıklayabilirsiniz. Ayrıca, bir çözüm adı seçebilir veya yeni projeyi bir git deposuna ekleyebilirsiniz ( **kaynak denetimine Ekle**' yi seçerek).

Çözümü ve projeyi oluşturmak için **Tamam** ' ı tıklatın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Yeni proje oluştur sayfasını açın

Visual Studio 2019 ' de yeni bir proje oluşturmanın birden çok yolu vardır. Visual Studio ilk kez açtığınızda, başlangıç penceresi görünür ve buradan **yeni proje oluştur**' u seçebilirsiniz.

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019 ' de başlangıç penceresinden ' yeni proje oluştur ' iletişim kutusunun ekran görüntüsü":::

Visual Studio geliştirme ortamı zaten açıksa,   >  menü çubuğunda dosya **yeni**  >  **Project** ' ni seçerek yeni bir proje oluşturabilirsiniz. ayrıca, araç çubuğundaki **yeni Project** düğmesine tıklayabilir veya **Ctrl** + **shıft** + **N**' ye basabilirsiniz.

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Visual Studio 2019 ' deki yeni Project düğmesinin ekran görüntüsü.":::

## <a name="select-a-template-type"></a>Şablon türü seçin

**Yeni proje oluştur** sayfasında, son seçtiğiniz şablonların listesi solda görüntülenir. Şablonlar *en son kullanılanlar* tarafından sıralanır.

son kullanılan şablonlardan seçim yapmadıysanız, tüm kullanılabilir proje şablonlarını **dile** göre (örneğin, C# veya C++), **platformu** (örneğin, Windows veya Azure) ve **Project türünü** (örneğin, masaüstü veya Web) filtreleyebilirsiniz. Şablonları daha fazla filtrelemek için arama kutusuna arama metni de girebilirsiniz, örneğin, **ASP.net**.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Visual Studio 2019 ' deki proje şablonu filtrelerinin ekran görüntüsü.":::

her şablon altında görüntülenen etiketler üç açılan listeye (dil, Platform ve Project türü) karşılık gelir.

> [!TIP]
> Aradığınız şablonu görmüyorsanız, Visual Studio için bir iş yükünüz eksik olabilir. örneğin, **Azure geliştirme** veya **.net ile mobil geliştirme** gibi ek iş yükleri yüklemek için Visual Studio Yükleyicisi açmak üzere **daha fazla araç ve özellik yüklemesi** bağlantısına tıklayın. Buradan, yüklemek istediğiniz iş yüklerini seçin ve ardından **Değiştir**' i seçin. Bundan sonra, ek proje şablonları arasından seçim yapabileceğiniz şekilde sunulacaktır.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Visual Studio 2019 ' deki ' daha fazla araç ve özellik yüklemesi ' bağlantısının ekran görüntüsü.":::

Bir şablon seçin ve ardından **İleri**' ye tıklayın.

## <a name="configure-your-project"></a>Projenizi yapılandırma

**Yeni projenizi yapılandırma** sayfasında projenize (ve çözümüne) ad vermek için kullanabileceğiniz seçenekler bulunur, bir disk konumu seçebilir ve bir çerçeve sürümü (seçtiğiniz şablona uygunsa) seçin.

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019 ' de ' yeni projenizi yapılandırın ' sayfasının ekran görüntüsü.":::

> [!NOTE]
> Visual Studio bir projeniz veya çözümünüz zaten varsa yeni bir proje oluşturursanız, ek bir yapılandırma seçeneği kullanılabilir. Yeni bir çözüm oluşturmayı veya zaten açık olan çözüme yeni projeyi eklemeyi seçebilirsiniz.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Visual Studio 2019 ' deki ' yeni çözüm oluştur ' veya ' çözüme ekle ' iletişim kutusunun ekran görüntüsü.":::

Yeni projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Çözüme ek projeler ekleme

bir çözüme ek bir proje eklemek istiyorsanız, **Çözüm Gezgini** ' deki çözüm düğümüne sağ tıklayın ve ardından   >  **yeni Project** ekle ' yi seçin.

> [!TIP]
> Sıfırdan oluşturulmuş bir proje ve çözüm örneği için adım adım yönergeler ve örnek kodla birlikte, bkz. [projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md)
- [Çözüm ve projelerle çalışma](creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [proje oluşturma (Mac için Visual Studio)](/visualstudio/mac/create-new-projects)
