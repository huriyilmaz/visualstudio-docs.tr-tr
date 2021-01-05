---
title: Yeni proje oluşturma
description: Visual Studio 'da yeni bir proje oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/23/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcbf39be441ba8237520fcc56ceec7946d688901
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846903"
---
# <a name="create-a-new-project-in-visual-studio"></a>Visual Studio 'da yeni proje oluşturma

Bu makalede, Visual Studio 'da hızlı bir şekilde yeni bir proje oluşturmayı göstereceğiz.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Yeni proje iletişim kutusunu aç

Visual Studio 2017 ' de yeni bir proje oluşturmanın birden çok yolu vardır. Başlangıç sayfasında, proje **şablonları ara** kutusuna bir proje şablonunun adını yazabilir veya yeni proje **Oluştur** bağlantısını seçerek **Yeni proje** iletişim kutusunu açabilirsiniz. Başlangıç sayfasından, menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje** ' yi de seçebilir veya araç çubuğunda **Yeni proje** düğmesine tıklayabilirsiniz.

![Visual Studio 'da dosya > yeni > proje seçenekleri seçili olan menü çubuğunun ekran görüntüsü.](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Şablon türü seçin

**Yeni proje** iletişim kutusunda, kullanılabilir proje şablonları **Şablonlar** kategorisi altındaki bir listede görüntülenir. Şablonlar programlama diline ve Visual C#, JavaScript ve Azure Data Lake gibi proje türüne göre düzenlenir.

![Yeni proje iletişim kutusunun yüklü şablonlar listesini gösteren ekran görüntüsü.](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Görüntülenen kullanılabilir dillerin ve proje şablonlarının listesi, çalıştırdığınız Visual Studio sürümüne ve yüklü iş yüklerine bağlıdır. Ek iş yüklerini nasıl yükleyeceğiniz hakkında bilgi edinmek için bkz. [iş yüklerini ve bileşenleri ekleyerek veya kaldırarak Visual Studio 'Yu değiştirme](../install/modify-visual-studio.md).

Dil adının yanındaki üçgeni tıklatıp ardından bir proje kategorisi (Windows Masaüstü gibi) seçerek kullanmak istediğiniz programlama diline ait şablonların listesini görüntüleyin.

Aşağıdaki görüntüde, Visual C# .NET Core projeleri için kullanılabilir proje şablonları gösterilmektedir:

![Aralarından seçim yapabileceğiniz proje şablonlarını listeleyen yeni proje iletişim kutusunun ekran görüntüsü.](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Projenizi yapılandırma

**Ad** kutusuna yeni proje için bir ad girin. Projeyi bilgisayarınızda varsayılan konuma kaydedebilir ya da başka bir konum bulmak için **tarayıcı** düğmesine tıklayabilirsiniz. Ayrıca, bir çözüm adı seçebilir veya yeni projeyi bir git deposuna ekleyebilirsiniz ( **kaynak denetimine Ekle**' yi seçerek).

Çözümü ve projeyi oluşturmak için **Tamam** ' ı tıklatın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Yeni proje oluştur sayfasını açın

Visual Studio 2019 ' de yeni bir proje oluşturmanın birden çok yolu vardır. Visual Studio 'yu ilk kez açtığınızda, başlangıç penceresi görüntülenir ve buradan **Yeni proje oluştur**' u seçebilirsiniz.

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019 ' de başlangıç penceresinden ' yeni proje oluşturma ' iletişim kutusunun ekran görüntüsü":::

Visual Studio geliştirme ortamı zaten açıksa,   >  menü çubuğunda Dosya **Yeni**  >  **Proje** ' yi seçerek yeni bir proje oluşturabilirsiniz. Araç çubuğundaki **Yeni proje** düğmesine de tıklayabilir veya **CTRL** + **SHIFT** + **N** tuşlarına basabilirsiniz.

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Visual Studio 2019 ' de yeni proje düğmesinin ekran görüntüsü.":::

## <a name="select-a-template-type"></a>Şablon türü seçin

**Yeni proje oluştur** sayfasında, son seçtiğiniz şablonların listesi solda görüntülenir. Şablonlar *en son kullanılanlar* tarafından sıralanır.

Son kullanılan şablonlardan seçim yapmadıysanız, tüm kullanılabilir proje şablonlarını **dile** göre (örneğin, C# veya C++), **platformu** (örneğin, Windows veya Azure) ve **proje türünü** (örneğin, masaüstü veya Web) göre filtreleyebilirsiniz. Şablonları daha fazla filtrelemek için arama kutusuna arama metni de girebilirsiniz, örneğin, **ASP.net**.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Visual Studio 2019 ' de proje şablonu filtrelerinin ekran görüntüsü.":::

Her şablon altında görüntülenen Etiketler üç açılan listeye (dil, platform ve proje türü) karşılık gelir.

> [!TIP]
> Aradığınız şablonu görmüyorsanız, Visual Studio için bir iş yükünüz eksik olabilir. Örneğin, **Azure geliştirme** veya **.NET ile mobil geliştirme** gibi ek iş yükleri yüklemek için Visual Studio yükleyicisi açmak üzere **daha fazla araç ve özellik yüklemesi** bağlantısına tıklayın. Buradan, yüklemek istediğiniz iş yüklerini seçin ve ardından **Değiştir**' i seçin. Bundan sonra, ek proje şablonları arasından seçim yapabileceğiniz şekilde sunulacaktır.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Visual Studio 2019 ' de ' daha fazla araç ve özellik yüklemesi ' bağlantısının ekran görüntüsü.":::

Bir şablon seçin ve ardından **İleri**' ye tıklayın.

## <a name="configure-your-project"></a>Projenizi yapılandırma

**Yeni projenizi yapılandırma** sayfasında projenize (ve çözümüne) ad vermek için kullanabileceğiniz seçenekler bulunur, bir disk konumu seçebilir ve bir çerçeve sürümü (seçtiğiniz şablona uygunsa) seçin.

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019 ' de ' yeni projenizi yapılandırma ' sayfasının ekran görüntüsü.":::

> [!NOTE]
> Visual Studio 'da zaten açık bir proje veya çözümünüz varsa yeni bir proje oluşturursanız, ek bir yapılandırma seçeneği kullanılabilir. Yeni bir çözüm oluşturmayı veya zaten açık olan çözüme yeni projeyi eklemeyi seçebilirsiniz.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Visual Studio 2019 ' de ' yeni çözüm oluştur ' veya ' çözüme Ekle ' iletişim kutusunun ekran görüntüsü.":::

Yeni projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Çözüme ek projeler ekleme

Bir çözüme ek bir proje eklemek istiyorsanız, **Çözüm Gezgini** ' deki çözüm düğümüne sağ tıklayın ve ardından   >  **Yeni proje** Ekle ' yi seçin.

> [!TIP]
> Sıfırdan oluşturulmuş bir proje ve çözüm örneği için adım adım yönergeler ve örnek kodla birlikte, bkz. [projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md)
- [Çözüm ve projelerle çalışma](creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [Proje oluşturma (Mac için Visual Studio)](/visualstudio/mac/create-new-projects)