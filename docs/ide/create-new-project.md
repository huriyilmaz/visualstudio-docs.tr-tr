---
title: Yeni proje oluşturma
description: Yeni bir proje oluşturma hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/24/2021
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
ms.openlocfilehash: 31955aa0cff228af34df5cc7dc8772feb4a3454b
ms.sourcegitcommit: 17202f3ac3f7f17ce3756b57dd56321f7254d1dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "133093039"
---
# <a name="create-a-new-project-in-visual-studio"></a>Visual Studio'de yeni proje oluşturma

Bu makalede, şablondan hızla yeni bir proje oluşturma Visual Studio göstereceğiz.

::: moniker range="vs-2017"

## <a name="open-the-new-project-page-in-visual-studio-2017"></a>Visual Studio 2017'de Yeni Project sayfasını açın

Visual Studio 2017'de yeni proje oluşturmanın birden çok yolu vardır. Başlangıç sayfasında, Proje şablonlarını ara kutusuna bir proje  şablonunun adını yazabilirsiniz  veya Yeni proje oluştur bağlantısını seçerek Yeni proje oluştur **iletişim Project** açabilirsiniz. Başlat sayfasının yanı sıra, menü **çubuğunda** Dosya Yeni Project'ı veya  >    >   araç **çubuğundaki Yeni** Project düğmesini de seçebilirsiniz.

![Dosya Adı Yeni dosya seçenekleri Visual Studio menü çubuğunun > > Project görüntüsü.](./media/vside-newproject1.png)

## <a name="select-a-template-type-in-visual-studio-2017"></a>Visual Studio 2017'de şablon türü seçme

Yeni **Project** iletişim kutusunda, kullanılabilir proje şablonları Şablonlar kategorisi altındaki bir **listede** görünür. Şablonlar Programlama diline ve Visual C#, JavaScript ve Azure Data Lake gibi proje türüne göre düzenlenmiştir.

![Yüklü şablonların listesini Project Yeni YüklemeLer iletişim kutusunun ekran görüntüsü.](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Görüntülenen kullanılabilir dillerin ve proje şablonlarının listesi, Visual Studio ve yüklü iş yüklerinin sürümüne bağlıdır. Ek iş yüklerini yükleme hakkında bilgi edinmek için [bkz. İş Visual Studio ve bileşenleri ekleyerek veya](../install/modify-visual-studio.md)kaldırarak verileri değiştirme.

Dil adının yanındaki üçgeni ve ardından bir proje kategorisini (Windows Desktop gibi) seçerek kullanmak istediğiniz programlama diline yönelik şablon listesini görüntüleyin.

Aşağıdaki görüntüde Visual C# .NET Core projeleri için kullanılabilen proje şablonları yer almaktadır:

![Seçebilirsiniz proje Project Listele iletişim kutusunun ekran görüntüsü.](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project-in-visual-studio-2017"></a>Visual Studio 2017'de projenizi yapılandırma

Ad kutusuna yeni proje için bir **ad** girin. Projeyi bilgisayarınızda varsayılan konuma kaydedebilir veya gözat düğmesini seçerek **başka** bir konum bulabilirsiniz. Bir çözüm adı da seçebilirsiniz veya yeni projeyi Git deposuna eklemek için (Kaynak Denetimine **Ekle'yi seçerek).**

Çözümü **ve** projeyi oluşturmak için Tamam'ı seçin.

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-the-create-a-new-project-dialog"></a>"Yeni proje oluştur" iletişim kutusunu açın

Yeni bir proje oluşturmak için birden çok yol vardır Visual Studio. İlk kez Visual Studio penceresi açılır ve buradan Yeni proje **oluştur'a tıklayın.**

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019'da başlangıç penceresindeki 'Yeni proje oluştur' iletişim kutusunun ekran görüntüsü":::

Geliştirme Visual Studio zaten açıksa, menü çubuğunda Dosya Yeni Dosya'Project   >    >  **yeni** bir proje oluşturabilirsiniz. Ayrıca, araç çubuğundaki **Yeni Project** düğmesini de seçerek veya Ctrl Shift N  + **tuşlarına** + **basabilirsiniz.**

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Visual Studio 2019'daki Yeni Project düğmesinin ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2022"

## <a name="open-the-create-a-new-project-dialog"></a>"Yeni proje oluştur" iletişim kutusunu açın

Yeni bir proje oluşturmak için birden çok yol vardır Visual Studio. İlk kez Visual Studio penceresi açılır ve buradan Yeni proje **oluştur'a tıklayın.**

:::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Visual Studio 2022'de başlangıç penceresindeki 'Yeni proje oluştur' iletişim kutusunun ekran görüntüsü.":::

Geliştirme Visual Studio zaten açıksa, menü çubuğunda Dosya Yeni Dosya'Project   >    >  **yeni** bir proje oluşturabilirsiniz. Ayrıca, araç çubuğundaki **Yeni Project** düğmesini de seçerek veya Ctrl Shift N  + **tuşlarına** + **basabilirsiniz.**

:::image type="content" source="media/vs-2022/new-project-button.png" alt-text="Visual Studio 2022'de Yeni Project düğmesinin ekran görüntüsü.":::

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="select-a-template-type"></a>Şablon türü seçme

Yeni **proje oluştur iletişim** kutusunda, sol tarafta son seçtiğiniz şablonların listesi görüntülenir. Şablonlar en son kullanılana *göre sıralanmış.*

Son kullanılan şablonlardan seçim yoksa, kullanılabilir tüm proje şablonlarını **Dil** (örneğin, C# veya C++), **Platform** (örneğin, Windows veya Azure) ve Project türüne (örneğin, Masaüstü veya **Web)** göre filtre kullanabilirsiniz. Şablonları daha fazla filtrelemek için arama kutusuna arama metni de girebilirsiniz, **örneğin,** asp.net.

::: moniker-end

::: moniker range="vs-2019"

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Visual Studio 2019'daki proje şablonu filtrelerinin ekran görüntüsü.":::

Her şablonun altında görünen etiketler üç açılan filtreye (Dil, platform ve proje türü) karşılık gelir.

> [!TIP]
> Kullanmak istediğiniz şablonu görmüyorsanız, uygulama için bir iş yükünüz eksik Visual Studio. **.NET** ile **Azure** Geliştirme veya Mobil Geliştirme gibi ek iş  yüklerini yüklemek için Daha fazla araç ve özellik yükle bağlantısını seçerek Visual Studio Yükleyicisi. Buradan yüklemek istediğiniz iş yüklerini seçin ve ardından Değiştir'i **seçin.** Bundan sonra, seçim yapmak için ek proje şablonları kullanılabilir.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Visual Studio 2019'da 'Daha fazla araç ve özellik yükle' bağlantısının ekran görüntüsü.":::

Bir şablon seçin ve ardından Sonraki'yi **seçin.**

::: moniker-end

::: moniker range="vs-2022"

:::image type="content" source="media/vs-2022/create-new-project-filters.png" alt-text="Visual Studio 2022'de proje şablonu filtrelerinin ekran görüntüsü.":::

Her şablonun altında görünen etiketler üç açılan filtreye (Dil, platform ve proje türü) karşılık gelir.

> [!TIP]
> Kullanmak istediğiniz şablonu görmüyorsanız, uygulama için bir iş yükünüz eksik Visual Studio. **.NET** ile **Azure** Geliştirme veya Mobil Geliştirme gibi ek iş  yüklerini yüklemek için Daha fazla araç ve özellik yükle bağlantısını seçerek Visual Studio Yükleyicisi. Buradan yüklemek istediğiniz iş yüklerini seçin ve ardından Değiştir'i **seçin.** Bundan sonra, seçim yapmak için ek proje şablonları kullanılabilir.
>
> :::image type="content" source="../get-started/csharp/media/vs-2022/not-finding-what-looking-for.png" alt-text="Visual Studio 2022'de 'Daha fazla araç ve özellik yükle' bağlantısının ekran görüntüsü.":::

Bir şablon seçin ve ardından Sonraki'yi **seçin.**

::: moniker-end

::: moniker range="vs-2019"

## <a name="configure-your-new-project"></a>Yeni projenizi yapılandırma

Yeni **projenizi yapılandır iletişim** kutusunda projenizi (ve çözüme) ad ve ardından bir disk konumu seçin ve bir Framework sürümü seçin (seçtiğiniz şablon için uygunsa) seçenekleri vardır.

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019'da 'Yeni projenizi yapılandır' iletişim kutusunun ekran görüntüsü.":::

> [!NOTE]
> Projeniz veya çözümünüz açık olduğunda yeni bir proje Visual Studio ek bir yapılandırma seçeneği kullanılabilir. Yeni bir çözüm oluşturabilir veya yeni projeyi zaten açık olan çözüme eklemeyi seçebilirsiniz.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="2019'da 'Yeni çözüm oluştur' veya 'Çözüme ekle' iletişim kutusunun Visual Studio görüntüsü.":::

Yeni **projeyi** oluşturmak için Oluştur'a seçin.

::: moniker-end

::: moniker range="vs-2022"

## <a name="configure-your-new-project"></a>Yeni projenizi yapılandırma

Yeni **projenizi yapılandır iletişim** kutusunda projenizi (ve çözüme) ad ve ardından bir disk konumu seçin ve bir Framework sürümü seçin (seçtiğiniz şablon için uygunsa) seçenekleri vardır.

:::image type="content" source="media/vs-2022/configure-new-project.png" alt-text="Visual Studio 2022'de 'Yeni projenizi yapılandır' iletişim kutusunun ekran görüntüsü.":::

Ek **bilgiler iletişim** kutusunda Bir Framework sürümü, kimlik doğrulama türü ve daha fazlasını seçme seçenekleri yer alıyor.

:::image type="content" source="media/vs-2022/aspnet-core-additional-information-dialog.png" alt-text="Visual Studio 2022'de 'Ek Bilgiler iletişim kutusunun ekran görüntüsü.":::

Yeni **projeyi** oluşturmak için Oluştur'a seçin.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Çözüme başka projeler ekleme

Bir çözüme başka bir proje eklemek için, Çözüm Gezgini'de çözüm düğümüne sağ **tıklayın ve**  >  Project.

> [!TIP]
> Sıfırdan oluşturulan bir proje ve çözüm örneği için, adım adım yönergeler ve örnek kod ile eksiksiz bir örnek için [bkz. Projelere ve çözümlere giriş.](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md)
- [Çözüm ve projelerle çalışma](creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [Proje oluşturma (Mac için Visual Studio)](/visualstudio/mac/create-new-projects)
